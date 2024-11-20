# PERNBACKEND

# Express.js  
## Import     
    import express from "express";  
## Creating the app     
    const app = express();  
## (GET) request any resource from the server     
    app.get("/",(req,res)=>{         
        res.send("Hello, World! My name is rohan I am from bagalkot");     
    })  
## (listen) starting the server in the specified port     
    app.listen(3000,()=>{         
        console.log(`Server is running on port ${3000}`);     
    })
