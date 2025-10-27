<!-- index.html -->
<div class="slider">
  <div class="slides">
    <img src="img1.jpg" alt="Image 1" />
    <img src="img2.jpg" alt="Image 2" />
    <img src="img3.jpg" alt="Image 3" />
  </div>
  <button id="prev">&#10094;</button>
  <button id="next">&#10095;</button>
</div>

/* style.css */
.slider {
  position: relative;
  width: 100%;
  max-width: 600px;
  margin: 40px auto;
  overflow: hidden;
  border-radius: 8px;
}
.slides {
  display: flex;
  transition: transform 0.5s ease-in-out;
}
.slides img {
  width: 100%;
  height: auto;
  flex-shrink: 0;
}
button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: #fff;
  border: none;
  font-size: 24px;
  cursor: pointer;
  z-index: 10;
}
#prev { left: 10px; }
#next { right: 10px; }

// script.js
const slides = document.querySelector('.slides');
const images = document.querySelectorAll('.slides img');
const prevBtn = document.getElementById('prev');
const nextBtn = document.getElementById('next');

let currentIndex = 0;

function showSlide(index) {
  if (index < 0) index = images.length - 1;
  if (index >= images.length) index = 0;
  slides.style.transform = `translateX(-${index * 100}%)`;
  currentIndex = index;
}

prevBtn.onclick = () => showSlide(currentIndex - 1);
nextBtn.onclick = () => showSlide(currentIndex + 1);

// Auto-play functionality
setInterval(() => showSlide(currentIndex + 1), 3000);

// Initial display
showSlide(0);
