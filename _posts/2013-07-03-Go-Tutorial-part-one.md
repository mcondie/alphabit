---
published: true
layout: default
title:  "Go Web Application Tutorial"
date:   2013-07-03 19:30:00
categories: web
---

One of the best features of Go is that the components needed to build an entire web stack are included as core libraries. Unlike languages such as java or ruby, there isn't a strong need for a framework to make web development tractable. That said, I spent a fair bit of time researching and experimenting to get a web application up and running the way I would like. Hopefully this tutorial helps you speed up the process. 

####Creating the server

First import the packages 'net/http', 'log', and 'io'. 'net/http' is the built in Go http library, including a full http server. 'log' is self explanitory. We'll use 'io' to write text to the http request. 

    package main
    import(
      "net/http"
      "log"
      "io"
    )

Next lets define and instantiate our server. 

    func main(){
      http.HandleFunc("/home", home_index)
      err:= http.ListenAndServe(":8080", nil)
      if err != nil{
        log.Fatal("ListenAndServe: ", err.Error())
      }
    }

The first call 'http.HandleFunc("/home", home_index)' is a basic route mapping function. It just tells the http server to use the function 'home_index' to respond to any request for the uri '/home'. 

Next is the call to start the http server. You can specify a domain and port like 'localhost:8080' however I just specify the port ':8080' so that it responds to traffic from outsite my VM. 

Finally, there is some boilerplate logging code. 

####Defining the handler

In our main function we passed a function name to the http server, which we need to implement before we compile and run the application.

    func home_index(w http.ResponseWriter, request *http.Request){
      w.Header().Set("Content-Type", "text/html")
      io.WriteString(w, "hello world")
    }

We set an http header parameter, then write the string "hello world" to the response writer.

####All Together

    package main
    import(
      "net/http"
      "log"
      "io"
    )

    func main(){
      http.HandleFunc("/home", home_index)
      err:= http.ListenAndServe(":8080", nil)
      if err != nil{
        log.Fatal("ListenAndServe: ", err.Error())
      }
    }

    func home_index(w http.ResponseWriter, request *http.Request){
      w.Header().Set("Content-Type", "text/html")
      io.WriteString(w, "hello world")
    }

Use the go commands to compile and run the application. Point your browser to <http://localhost:8080/home> to see the current application output.

Coming soon, forms, databases, and json...