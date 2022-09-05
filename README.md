# expressMDN
Solution to the MDN Express tutorial (w/ Pug, async, MongoDB and others)

### Gist 

#### Tip: if you get lost, look at how the data flows.

1.app.js -> main setup point
    
    import 'backend' (express, path, cookieParser, mongoose...)
    
    import routers (index, ... from "./routes/*")
    
    init a connection with DB (we used URL)
    
    connect to DB
    
    set up view engine 
    
    set up routers (w/ app.use('/*', routerObj)
    
    set up error page and handling 
    
    export

2. provide models/schemas in './models/*'
    
    mongoose
    
    new Schema 
    
    virtual functions 
    
    export
    
3. setup controllers

    import required models + async and validator 
    
    implement pages to display 
    
    implement form GET, POST on exports (if needed)
    
3.5 centralize routing in a catalog file

    import controllers

    redirect to '/catalog' or w/e from index
    
    router.get/post the URLs with exported controller functions 
    
4. setup views

    data is provided from controllers and models (e.g. virtuals)
    in response (.render) object
    
5. ...

6. Profit


### Questions 


Q: How do URL automatically use data-ids?

A.short: Route parameters captured in req.params.id

A.long: A virtual method is defined in the model `.virtual('url')`. The method is then used in the code 
to provide a string-URL that contains the _id property given my Mongo. When the controller provides the 
view engine with the data object, the property is used in the view template to make a request with
the URL that contains the _id. Finally, the routing catalog uses Route Parameters (captured in req.params.<name>)
and provides a page (or does smth) for a given data object.
