---
published: true
layout: default
title:  "Go Web Application - Forms"
date:   2013-07-03 19:40:00
categories: web, tutorials
---

Check out [part one](http://www.alphabitsoup.net/2013/07/03/Go-Tutorial-part-one/) of this tutorial to get a basic Go http server working.

####Serving up some html

Let's add some real html to the mix.

    const html = `<html><body><form action="#" method="post" name="theform"><input type="text" name="myText"/><input type="submit" value="Submit"/></form></html></body>`

And we'll add another request handler.

    func form_index(w http.ResponseWriter, request *http.Request){
      w.Header().Set("Content-Type", "text/html")
      io.WriteString(w, html)
    }

After you build and run the application, point your browser to <http://localhost:8080/form>, and you should see page with a text box and a button.

####POST handling

Now we'll modify the request handler to process the input from the form.

    func form_index(w http.ResponseWriter, request *http.Request){
      w.Header().Set("Content-Type", "text/html")
      switch request.Method{
      case "GET":
        io.WriteString(w, html)
      case "POST":
        io.WriteString(w, request.FormValue("myText"))
      }
    }

####All Together

    package main
    import(
      "net/http"
      "log"
      "io"
    )

    func main(){
      http.HandleFunc("/home", home_index)
      http.HandleFunc("/form", form_index)
      err:= http.ListenAndServe(":8080", nil)
      if err != nil{
        log.Fatal("ListenAndServe: ", err.Error())
      }
    }

    func home_index(w http.ResponseWriter, request *http.Request){
      w.Header().Set("Content-Type", "text/html")
      io.WriteString(w, "hello world")
    }

    const html = `<html><body><form action="#" method="post" name="theform"><input type="text" name="myText"/><input type="submit" value="Submit"/></form></html></body>`

    func form_index(w http.ResponseWriter, request *http.Request){
      w.Header().Set("Content-Type", "text/html")
      switch request.Method{
      case "GET":
        io.WriteString(w, html)
      case "POST":
        io.WriteString(w, request.FormValue("myText"))
      }
    }