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
## Middleware
### .sendFile() function
#### imports
    import {dirname} from "path";
    import {fileURLToPath} from "url";
    const __dirname = dirname(fileURLToPath(import.meta.url));
#### using
    app.get("/",(req,res)=>{
        res.sendFile(__dirname +"/public/index.html");
    });
### bodyParser
#### step1.
    use npm to install the body-parser module (npm i body-parser)
#### step2. Import the body parser module
    import bodyParser from "body-parser";
#### step3. Mount the middleware using the express.use
    app.use
#### step4. Specify .urlencoded ({extended:true}) to create a body for URL-encoded requests like our form submission.
    app.use(bodyParser.urlencoded({extended:true}));
#### step5. Write a .post("/submit") handler where you console.log() the form contents when the user clicks on the submit button
    app.post("/submit",(req,res)=>{
        console.log(req.body);
    });

## (listen) starting the server in the specified port     
    app.listen(3000,()=>{         
        console.log(`Server is running on port ${3000}`);     
    })

## example of custom middleware program 

    import express from "express";
    import bodyParser from "body-parser";
    import { dirname } from "path";
    import { fileURLToPath } from "url";
    const __dirname = dirname(fileURLToPath(import.meta.url));
    
    const app = express();
    const port = 3000;
    
    var isAuthorized = false;
    
    app.use(bodyParser.urlencoded({extended:true}));
    
    function passwordCheck(req,res,next){
        const password = req.body["password"];
        if(password === "ILoveRohan"){
            isAuthorized = true;
        }else{
            isAuthorized = false;
        }
        next();
    }
    
    app.use(passwordCheck);
    
    app.get("/", (req,res)=>{
        res.sendFile(__dirname+"/public/index.html");
    });
    
    app.post("/rohan",(req,res) =>{
        if(isAuthorized){
            res.sendFile(__dirname+"/public/secret.html");
        }else{
            res.sendFile(__dirname+"/public/index.html");
        }
    });
    
    app.listen(port,()=>{
        console.log(`Listening on port ${port}`);
    })

    
