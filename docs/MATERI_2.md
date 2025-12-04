# Video 2 | Router

## Router
- Inti dari library HttpRouter adalah struct Router
- Router ini merupakan implementasi dari http.Handler, sehingga kita bisa dengan mudah menambahkan ke dalam http.Server
- Untuk membuat Router, kita bisa menggunakan function httprouter.New(), yang akan mengembalikan Router pointer

## HTTP Method
- Router mirip dengan ServeMux, dimana kita bisa menambahkan route ke dalam Router
- Kelebihan dibandingkan dengan ServeMux adalah, pada Router, kita bisa menentukan HTTP Method yang ingin kita gunakan, misal GET, POST, PUT, dan lain-lain
- Cara menambahkan route ke dalam Router adalah gunakan function yang sama dengan HTTP Method nya, misal router.GET(), router.POST(), dan lain-lain

## httprouter.Handle
- Saat kita menggunakan ServeMux, ketika menambah route, kita bisa menambahkan http.Handler
- Berbeda dengan Router, pada Router kita tidak menggunakan http.Handler lagi, melainkan menggunakan type httprouter.Handle
- Perbedaan dengan http.Handler adalah, pada httprouter.Handle, terdapat parameter ke tiga yaitu Params, yang akan kita bahas nanti di chapter tersendiri

## Kode Program
```go
package learngolanghttprouter

import (
	"fmt"
	"io"
	"net/http"
	"net/http/httptest"
	"testing"

	"github.com/julienschmidt/httprouter"
	"github.com/stretchr/testify/assert"
)

func TestRouter(t *testing.T) {
	router := httprouter.New()
	router.GET("/", func(w http.ResponseWriter, r *http.Request, p httprouter.Params) {
		fmt.Fprint(w, "Hello World")
	})

	request := httptest.NewRequest("GET", "http://localhost:3000/", nil)
	recorder := httptest.NewRecorder()

	router.ServeHTTP(recorder, request)

	response := recorder.Result()
	body, _ := io.ReadAll(response.Body)

	assert.Equal(t, "Hello World", string(body))
}
```