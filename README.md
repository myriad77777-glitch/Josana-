index.html
https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Josana Day Academy</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>
body { margin:0; font-family:'Poppins',sans-serif; background:#f5f7fa; }

/* NAV */
nav {
  display:flex; justify-content:space-between;
  padding:15px 40px; background:white;
  position:sticky; top:0; z-index:1000;
}
nav a { margin:0 10px; text-decoration:none; color:#333; }

/* SLIDER */
.slider { position:relative; height:90vh; overflow:hidden; }
.slide {
  position:absolute; width:100%; height:100%;
  opacity:0; transition:1s;
}
.slide img { width:100%; height:100%; object-fit:cover; }
.slide.active { opacity:1; }

.caption {
  position:absolute; top:50%; left:50%;
  transform:translate(-50%,-50%);
  color:white; text-align:center;
}

.glass {
  background:rgba(0,0,0,0.4);
  backdrop-filter:blur(10px);
  padding:20px;
  border-radius:10px;
}

/* ARROWS */
.prev,.next {
  position:absolute; top:50%;
  transform:translateY(-50%);
  background:rgba(0,0,0,0.5);
  color:white; border:none;
  padding:10px; cursor:pointer;
}
.prev { left:20px; }
.next { right:20px; }

/* DOTS */
.dots {
  position:absolute; bottom:20px;
  width:100%; text-align:center;
}
.dots span {
  width:10px; height:10px;
  display:inline-block;
  background:white;
  margin:5px;
  border-radius:50%;
  opacity:0.5;
  cursor:pointer;
}
.dots .active { opacity:1; }

/* SECTION */
.section {
  padding:70px 20px;
  text-align:center;
  opacity:0;
  transform:translateY(40px);
  transition:0.8s;
}
.section.show {
  opacity:1;
  transform:translateY(0);
}

/* GRID */
.grid {
  display:flex; flex-wrap:wrap;
  justify-content:center;
}
.card {
  background:white;
  margin:15px; padding:20px;
  width:260px;
  border-radius:12px;
  box-shadow:0 5px 20px rgba(0,0,0,0.1);
}

/* GALLERY */
.gallery img {
  width:300px;
  margin:10px;
  border-radius:10px;
}

/* FORM */
form { max-width:400px; margin:auto; }
input,textarea {
  width:100%; padding:10px;
  margin:10px 0;
}
button.submit {
  background:#003366;
  color:white;
  border:none;
  padding:10px;
}

/* FOOTER */
footer {
  background:#001a33;
  color:white;
  text-align:center;
  padding:20px;
}
</style>
</head>

<body>

<nav>
  <h2>Josana Academy</h2>
  <div>
    <a href="#">Home</a>
    <a href="#gallery">Gallery</a>
    <a href="#admissions">Admissions</a>
  </div>
</nav>

<!-- SLIDER -->
<div class="slider">

<div class="slide active">
<img src="https://images.unsplash.com/photo-1509062522246-3755977927d7">
<div class="caption glass">
<h1>Inspiring Excellence</h1>
<p>Building Future Leaders</p>
</div>
</div>

<div class="slide">
<img src="https://images.unsplash.com/photo-1588072432836-e10032774350">
<div class="caption glass">
<h1>Modern Learning</h1>
<p>Empowering Every Student</p>
</div>
</div>

<div class="slide">
<img src="https://images.unsplash.com/photo-1577896851231-70ef18881754">
<div class="caption glass">
<h1>Admissions Open</h1>
<p>Join Us Today</p>
</div>
</div>

<button class="prev">❮</button>
<button class="next">❯</button>

<div class="dots"></div>

</div>

<!-- PROGRAMS -->
<div class="section">
<h2>Our Programs</h2>
<div class="grid">
<div class="card">CBC Curriculum</div>
<div class="card">Primary Education</div>
<div class="card">Co-Curricular Activities</div>
</div>
</div>

<!-- GALLERY -->
<div class="section gallery" id="gallery">
<h2>Gallery</h2>
<img src="https://images.unsplash.com/photo-1588072432836-e10032774350">
<img src="https://images.unsplash.com/photo-1509062522246-3755977927d7">
<img src="https://images.unsplash.com/photo-1577896851231-70ef18881754">
</div>

<!-- FORM -->
<div class="section" id="admissions">
<h2>Apply Now</h2>

<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
<input type="text" name="name" placeholder="Student Name" required>
<input type="email" name="email" placeholder="Parent Email" required>
<textarea name="message" placeholder="Details"></textarea>
<button class="submit">Submit Application</button>
</form>

</div>

<footer>
<p>© 2026 Josana Day Academy</p>
</footer>

<!-- WHATSAPP -->
<a href="https://wa.me/254XXXXXXXXX"
style="position:fixed;bottom:20px;right:20px;
background:#25D366;color:white;padding:15px;
border-radius:50%;">💬</a>

<script>
let slides=document.querySelectorAll('.slide');
let index=0;
let dotsContainer=document.querySelector('.dots');

/* dots */
slides.forEach((_,i)=>{
 let dot=document.createElement('span');
 dot.onclick=()=>{index=i;show();}
 dotsContainer.appendChild(dot);
});

let dots=document.querySelectorAll('.dots span');

function show(){
 slides.forEach(s=>s.classList.remove('active'));
 dots.forEach(d=>d.classList.remove('active'));
 slides[index].classList.add('active');
 dots[index].classList.add('active');
}

document.querySelector('.next').onclick=()=>{
 index=(index+1)%slides.length; show();
};

document.querySelector('.prev').onclick=()=>{
 index=(index-1+slides.length)%slides.length; show();
};

setInterval(()=>{
 index=(index+1)%slides.length; show();
},5000);

show();

/* scroll animation */
let sections=document.querySelectorAll('.section');

window.addEventListener('scroll',()=>{
 sections.forEach(sec=>{
  let pos=sec.getBoundingClientRect().top;
  if(pos<window.innerHeight-100){
    sec.classList.add('show');
  }
 });
});
</script>

</body>
</html>
<section style="padding:40px; text-align:center;">
  <h2>Our Students</h2>
  <img src="images/students.jpg" alt="Josana Students" 
       style="width:90%; max-width:900px; border-radius:15px; box-shadow:0 10px 30px rgba(0,0,0,0.2);">
</section>
<img src="images/students.jpg">
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Josana Day School</title>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  line-height: 1.6;
}

/* NAVBAR */
nav {
  background: #0a2a66;
  color: white;
  padding: 15px;
  text-align: center;
  font-size: 20px;
}

/* HERO SECTION */
.hero {
  background: url('images/students.jpg') center/cover no-repeat;
  height: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  text-align: center;
}

.hero h1 {
  background: rgba(0,0,0,0.5);
  padding: 15px;
  border-radius: 10px;
}

/* SECTIONS */
.section {
  padding: 50px 20px;
  text-align: center;
}

.section h2 {
  margin-bottom: 20px;
}

/* IMAGE STYLE */
.section img {
  width: 90%;
  max-width: 900px;
  border-radius: 15px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

/* FOOTER */
footer {
  background: #0a2a66;
  color: white;
  text-align: center;
  padding: 20px;
}
</style>

</head>
<body>

<nav>
  Josana Day School
</nav>

<div class="hero">
  <h1>Welcome to Josana Day School</h1>
</div>

<div class="section">
  <h2>Our Students</h2>
  <img src="images/students.jpg" alt="Students">
  <p>We nurture excellence, discipline, and creativity in every student.</p>
</div>

<div class="section">
  <h2>About Us</h2>
  <p>Josana Day School is committed to providing quality education in a supportive environment.</p>
</div>

<footer>
  © 2026 Josana Day School
</footer>

</body>
</html>
