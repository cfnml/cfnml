<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LUCASIO - The Code</title>
  <style>
    body {
      margin: 0;
      background-color: #000;
      color: #f0f0f0;
      font-family: 'Helvetica Neue', sans-serif;
      overflow-x: hidden;
    }.enter-btn {
  border: 1px solid #fff;
  padding: 10px 30px;
  text-transform: uppercase;
  letter-spacing: 2px;
  background: transparent;
  color: white;
  font-weight: bold;
  cursor: pointer;
  margin: 50px auto;
  display: block;
  transition: all 0.3s ease;
}

.enter-btn:hover {
  background: white;
  color: black;
}

.symbols {
  display: flex;
  justify-content: center;
  gap: 40px;
  margin: 40px 0;
}

.symbols span {
  font-size: 28px;
  transition: transform 0.3s ease, color 0.3s ease;
  cursor: pointer;
}

.symbols span:hover {
  transform: scale(1.2);
  color: #ccc;
}

.section {
  text-align: center;
  padding: 60px 20px;
}

.section h2 {
  font-size: 36px;
  margin-bottom: 10px;
}

.section p {
  font-size: 18px;
  color: #bbb;
}

.image-row {
  display: flex;
  justify-content: center;
  gap: 40px;
  flex-wrap: wrap;
  margin-top: 40px;
}

.image-row img {
  max-width: 300px;
  border-radius: 8px;
  transition: transform 0.4s ease;
}

.image-row img:hover {
  transform: scale(1.05);
}

.slogan {
  font-size: 20px;
  font-weight: 300;
  margin-top: 10px;
  color: #aaa;
}

.fade-in {
  opacity: 0;
  transform: translateY(50px);
}

.zoom-in {
  opacity: 0;
  transform: scale(0.8);
  transition: opacity 0.8s ease, transform 0.8s ease;
}

.zoom-in.animate {
  opacity: 1;
  transform: scale(1);
}

.rotate-in {
  opacity: 0;
  transform: rotate(-10deg) scale(0.9);
  transition: opacity 1s ease, transform 1s ease;
}

.rotate-in.animate {
  opacity: 1;
  transform: rotate(0deg) scale(1);
}

.stagger-child {
  opacity: 0;
  transform: translateY(40px);
  transition: all 0.6s ease;
}

.stagger-child.visible {
  opacity: 1;
  transform: translateY(0);
}

  </style>
</head>
<body>
  <button class="enter-btn zoom-in">Enter</button>  <div class="symbols rotate-in">
    <span>&#9675;</span>
    <span>&#x16B1;</span>
    <span>|||</span>
    <span>&#128214;</span>
    <span>&#9904;</span>
  </div>  <div class="section fade-in">
    <h2>THE ORIGIN</h2>
    <div class="image-row stagger-fade">
      <img class="stagger-child" src="https://via.placeholder.com/300x300?text=Sketch" alt="Sketch">
      <img class="stagger-child" src="https://via.placeholder.com/300x300?text=LUCASIO+Tee" alt="T-shirt">
    </div>
  </div>  <div class="section fade-in">
    <h2>THE CODE</h2>
    <p class="slogan">OBEY THE CODE. WEAR THE TRUTH.</p>
    <div class="image-row stagger-fade">
      <img class="stagger-child" src="https://via.placeholder.com/300x300?text=Black+Tee" alt="Black Tee">
      <img class="stagger-child" src="https://via.placeholder.com/300x300?text=Premium+Design" alt="Premium Design">
    </div>
  </div>  <script>
    const observer = new IntersectionObserver(entries => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          if (entry.target.classList.contains('zoom-in')) {
            entry.target.classList.add('animate');
          } else if (entry.target.classList.contains('rotate-in')) {
            entry.target.classList.add('animate');
          } else if (entry.target.classList.contains('fade-in')) {
            entry.target.style.opacity = 1;
            entry.target.style.transform = 'translateY(0)';
            entry.target.style.transition = 'opacity 1s ease, transform 1s ease';
          } else if (entry.target.classList.contains('stagger-fade')) {
            const children = entry.target.querySelectorAll('.stagger-child');
            children.forEach((child, index) => {
              setTimeout(() => {
                child.classList.add('visible');
              }, index * 150);
            });
          }
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.1 });

    document.querySelectorAll('.zoom-in, .rotate-in, .fade-in, .stagger-fade').forEach(el => {
      observer.observe(el);
    });
  </script></body>
</html>
