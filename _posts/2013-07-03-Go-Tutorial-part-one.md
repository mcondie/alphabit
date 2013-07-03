---
published: false
layout: default
---

One of the best features of go is that the components needed to build an entire web stack are included as core libraries. Unlike languages such as java or ruby, there isn't a strong need for a framework to make web development tractable. That said, I spent a fair bit of time researching and experimenting to get a web application up and running the way I would like. Hopefully this tutorial helps you speed up the process. 

##Creating the server

<code>
package main
import(
  "net/http"
  "log"
  "io"
)

func main(){
  http.HandleFunc("/home", home_index)
  err:= http.ListenAndServe("localhost:8080", nil)
  if err != nil{
    log.Fatal("ListenAndServe: ", err.Error())
  }
}

func home_index(w http.ResponseWriter, request *http.Request){
  w.Header().Set("Content-Type", "text/html")
  io.WriteString(w, "hello world")
}
</code>
