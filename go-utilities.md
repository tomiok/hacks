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

```go
func Hash(s interface{}) int {
	var b bytes.Buffer
	gob.NewEncoder(&b).Encode(s)
	a :=  b.Bytes()
	c := 0
	res := 0
	for _, bb := range a {
		res += 31 * c +int(bb)
		c++
	}
	return res
}

func Test_h(t *testing.T) {
	fmt.Println(Hash2("hola"))
	fmt.Println(Hash2(1))
	fmt.Println(Hash2(struct {
		name string
	}{name: "tomas"}))
}
```
