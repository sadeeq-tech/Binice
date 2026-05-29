<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bince Social</title>

<style>
*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Arial;
}

body{
background:#111;
color:white;
}

header{
background:#000;
padding:15px;
display:flex;
justify-content:space-between;
align-items:center;
border-bottom:1px solid #333;
}

.logo{
font-size:24px;
font-weight:bold;
color:#00ff99;
}

.container{
max-width:600px;
margin:auto;
padding:20px;
}

.post-box{
background:#1e1e1e;
padding:15px;
border-radius:10px;
margin-bottom:20px;
}

textarea{
width:100%;
height:80px;
padding:10px;
border:none;
border-radius:10px;
outline:none;
resize:none;
font-size:16px;
}

button{
margin-top:10px;
padding:10px 20px;
border:none;
background:#00ff99;
color:black;
font-weight:bold;
border-radius:10px;
cursor:pointer;
}

.feed{
margin-top:20px;
}

.post{
background:#1e1e1e;
padding:15px;
border-radius:10px;
margin-bottom:15px;
}

.post h3{
margin-bottom:10px;
color:#00ff99;
}

.actions{
margin-top:10px;
display:flex;
gap:10px;
}

.dark-toggle{
cursor:pointer;
padding:8px 15px;
background:#222;
border-radius:10px;
}

.light{
background:#f2f2f2;
color:black;
}

.light header{
background:white;
color:black;
}

.light .post,
.light .post-box{
background:white;
color:black;
}

.light textarea{
background:#eee;
color:black;
}
</style>
</head>

<body>

<header>
<div class="logo">Bince Social</div>

<div class="dark-toggle" onclick="toggleMode()">
Dark Mode
</div>
</header>

<div class="container">

<div class="post-box">
<textarea id="postText" placeholder="What's happening?"></textarea>
<button onclick="createPost()">Post</button>
</div>

<div class="feed" id="feed"></div>

</div>

<script>

function createPost(){

let text = document.getElementById("postText").value;

if(text.trim() === ""){
alert("Write something");
return;
}

let post = document.createElement("div");
post.className = "post";

post.innerHTML = `
<h3>@user</h3>
<p>${text}</p>

<div class="actions">
<button onclick="likePost(this)">❤️ Like</button>
<button onclick="commentPost()">💬 Comment</button>
</div>
`;

document.getElementById("feed").prepend(post);

document.getElementById("postText").value = "";
}

function likePost(btn){

let likes = btn.getAttribute("data-like");

if(!likes){
likes = 0;
}

likes++;

btn.setAttribute("data-like", likes);

btn.innerHTML = `❤️ ${likes}`;
}

function commentPost(){
alert("Comment system coming soon");
}

function toggleMode(){
document.body.classList.toggle("light");
}

</script>

</body>
</html>
