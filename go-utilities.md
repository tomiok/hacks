### go generate random runes

```
const (
	runes     = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
	otpLength = 15
)

func startSeed() {
	rand.Seed(time.Now().UnixNano())
}

var letterRunes = []rune(runes)

func RandStringRunesStandard() string {
	return randStringRunes(otpLength)
}

func randStringRunes(n int) string {
	startSeed()
	b := make([]rune, n)
	for i := range b {
		b[i] = letterRunes[rand.Intn(len(letterRunes))]
	}
	return string(b)
}

```
