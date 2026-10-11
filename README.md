
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Bestie Quiz</title>
<style>
body{margin:0;background:#130f24;color:white;font-family:Arial;padding:22px}
main{max-width:480px;margin:auto}
h1{color:#d6a5ff}
.card{background:#241c3a;padding:20px;border-radius:18px}
input,button{box-sizing:border-box;width:100%;padding:13px;margin:8px 0;border-radius:9px;font-size:16px}
input{background:#151024;color:white;border:1px solid #665080}
button{background:#d6a5ff;border:0;font-weight:bold}
label{display:block;margin-top:15px}
</style>
</head>
<body>
<main>
<h1>💜 Bestie Quiz</h1>
<p>Who knows you best? Challenge your friends!</p>
<div class="card">
<label>Your name</label>
<input id="name" placeholder="Enter your name">
<label>My favourite food?</label>
<select id="food">
<option>Pizza</option><option>Momos</option>
<option>Biryani</option><option>Burger</option>
</select>
<label>My dream destination?</label>
<select id="place">
<option>Dubai</option><option>Goa</option>
<option>London</option><option>Japan</option>
</select>
<label>My favourite hobby?</label>
<select id="hobby">
<option>Gaming</option><option>Football</option>
<option>Music</option><option>Movies</option>
</select>
<button onclick="makeQuiz()">Create My Quiz ✨</button>
<div id="result"></div>
</div>
</main>
<script>
function makeQuiz(){
let name=document.getElementById('name').value.trim();
if(!name){alert('Enter your name first!');return;}
let data={
name:name,
food:document.getElementById('food').value,
place:document.getElementById('place').value,
hobby:document.getElementById('hobby').value
};
let url=location.href.split('#')[0]+'#quiz='+encodeURIComponent(JSON.stringify(data));
document.getElementById('result').innerHTML=
'<p>Your quiz link is ready!</p><input id="link" readonly><button onclick="copyLink()">Copy Link</button><button onclick="shareLink()">Share WhatsApp</button>';
document.getElementById('link').value=url;
}
function copyLink(){
let input=document.getElementById('link');
input.select();
if(navigator.clipboard){
navigator.clipboard.writeText(input.value).then(()=>alert('Link copied!'));
}else{alert('Select the link and copy it.');}
}
function shareLink(){
let link=document.getElementById('link').value;
location.href='https://wa.me/?text='+encodeURIComponent('Play my Bestie Quiz! '+link);
}
</script>
</body>
</html>
