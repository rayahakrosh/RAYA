const express = require('express');
const { dirname } = require('path');
const app= express();
const port = 3000;
app.use(express.json());
let students=[];
let nextID =1;

app.get('/',(req,res)=>{
    res.sendFile(__dirname+"/index.html")
});
app.get('/s/',(req,res)=>{
    res.json(students)
});
app.get('/s/:x',(req,res)=>{
    let name = req.params.x;
    let ip = req.ip;
    let id = nextID;
    let obj ={id,name,ip};
    students.push(obj)
    nextID++;
    res.json({message: "ok"})

});
app.listen(port,()=>{console.log(`http://localhost:${port}`)});
