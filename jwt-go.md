Adding a middleware for JWT

```go
package middleware

import (
	"errors"
	"github.com/dgrijalva/jwt-go"
	"github.com/go-chi/jwtauth"
	"net/http"
	"strings"
)

// Authenticator is a default authentication middleware to enforce access from the
// Verifier middleware request context values. The Authenticator sends a 401 Unauthorized
// response for any unverified tokens and passes the good ones through. It's just fine
// until you decide to write something similar and customize your client response.
func Authenticator(next http.Handler) http.Handler {
	return http.HandlerFunc(func(w http.ResponseWriter, r *http.Request) {
		token := TokenFromHeader(r)

		if token != "" {
			http.Error(w, http.StatusText(401), 401)
			return
		}

		// Token is authenticated, pass it through
		next.ServeHTTP(w, r)
	})
}

func VerifyRequest(ja *jwtauth.JWTAuth, r *http.Request, findTokenFns ...func(r *http.Request) string) (*jwt.Token, error) {
	var tokenStr string
	var err error

	// Extract token string from the request by calling token find functions in
	// the order they where provided. Further extraction stops if a function
	// returns a non-empty string.
	for _, fn := range findTokenFns {
		tokenStr = fn(r)
		if tokenStr != "" {
			break
		}
	}
	if tokenStr == "" {
		return nil, errors.New("no token")
	}

	// Verify the token
	token, err := ja.Decode(tokenStr)
	if err != nil {
		if verr, ok := err.(*jwt.ValidationError); ok {
			if verr.Errors&jwt.ValidationErrorExpired > 0 {
				return token, errors.New("token expired")
			} else if verr.Errors&jwt.ValidationErrorIssuedAt > 0 {
				return token, errors.New("IAT invalid")
			} else if verr.Errors&jwt.ValidationErrorIssuedAt > 0 {
				return token, errors.New("NBF invalid")
			}
		}
		return token, err
	}

	if token == nil || !token.Valid {
		return token, errors.New("token unauthorized")
	}

	// Valid!
	return token, nil
}

// TokenFromHeader tries to retreive the token string from the
// "Authorization" reqeust header: "Authorization: BEARER T".
func TokenFromHeader(r *http.Request) string {
	// Get token from authorization header.
	bearer := r.Header.Get("Authorization")
	if (len(bearer) > 7) && (strings.ToUpper(bearer[0:6]) == "BEARER") {
		return bearer[7:]
	}
	return ""
}

// contextKey is a value for use with context.WithValue. It's used as
// a pointer so it fits in an interface{} without allocation. This technique
// for defining context keys was copied from Go 1.7's new use of context in net/http.
type contextKey struct {
	name string
}

func (k *contextKey) String() string {
	return "jwtauth context value " + k.name
}

``` 
