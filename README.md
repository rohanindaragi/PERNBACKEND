# PERNBACKEND
# NPM
## Initialise npm
    npm init or npm init -y
## To install any node package
    npm i <something>
## To run any file 
    node <filename.extension>
    use nodemon to save the time
# Express.js  
## Import     
    import express from "express";  
## Creating the app     
    const app = express();  
## (GET) request any resource from the server     
    app.get("/",(req,res)=>{         
        res.send("Hello, World! My name is rohan I am from bagalkot");     
    })  
## different types of requests
    app.get("/",(req,res)=>{
        res.send("<h1>Hello</h1>");
    })
    
    app.post("/register", (req,res)=>{
        res.sendStatus(201);
    })
    
    app.put("/user/rohan", (req,res)=>{
        res.sendStatus(200);
    })
    
    app.patch("/user/rohan", (req,res)=>{
        res.sendStatus(200);
    })
    
    app.delete("/user/angela", (req,res)=>{
        res.sendStatus(200);
    })
## (listen) starting the server in the specified port     
    app.listen(3000,()=>{         
        console.log(`Server is running on port ${3000}`);     
    })
    
