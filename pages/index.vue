<template>
  <div class="landing-page">
    <!-- Left column: title + navigation -->
    <div class="landing-page__content">
      <div class="landing-page__link landing-page__link--title">
        Ali Fuat Sakaci
      </div>
      <nav class="landing-page__nav">
        <NuxtLink
          class="landing-page__link landing-page__link--portfolio"
          to="/home"
          >PORTFOLIO</NuxtLink
        >
        <NuxtLink
          class="landing-page__link landing-page__link--me"
          to="/portfolio"
          >ME</NuxtLink
        >
        <NuxtLink
          class="landing-page__link landing-page__link--about"
          to="/about"
          >ABOUT</NuxtLink
        >
        <NuxtLink
          class="landing-page__link landing-page__link--contact"
          to="/contact"
          >CONTACT</NuxtLink
        >
      </nav>
    </div>

    <!-- Right column: canvas-based slideshow -->
    <div class="landing-page__hero">
      <canvas ref="heroCanvas" class="landing-page__canvas"></canvas>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

// 1️⃣ Grab every JPG in assets/images
const modules = import.meta.glob('@/assets/images/*.jpg', {
  eager: true,
  import: 'default',
})
const imageURLs = Object.values(modules)

// 2️⃣ Refs & state
const heroCanvas = ref(null)
let ctx, cw, ch
let images = []      // HTMLImageElements
let current = 0      // current image index
let nextIndex = 0
let intervalId = null
let rafId = null     // for requestAnimationFrame

// 3️⃣ Resize helper
function resizeCanvas() {
  const canvas = heroCanvas.value
  cw = (canvas.width = canvas.clientWidth)
  ch = (canvas.height = canvas.clientHeight)
  ctx.clearRect(0, 0, cw, ch)
  if (images[current]?.complete) {
    ctx.drawImage(images[current], 0, 0, cw, ch)
  }
}

// 4️⃣ Slide animation
function startSlide() {
  nextIndex = (current + 1) % images.length
  const duration = 600 // ms
  const start = performance.now()

  function animate(time) {
    const t = Math.min((time - start) / duration, 1) // 0 → 1
    const offset = -t * cw

    ctx.clearRect(0, 0, cw, ch)
    ctx.drawImage(images[current], offset, 0, cw, ch)
    ctx.drawImage(images[nextIndex], offset + cw, 0, cw, ch)

    if (t < 1) {
      rafId = requestAnimationFrame(animate)
    } else {
      current = nextIndex
    }
  }

  rafId = requestAnimationFrame(animate)
}

// 5️⃣ Lifecycle
onMounted(() => {
  // create Image objects
  images = imageURLs.map((url) => {
    const img = new Image()
    img.src = url
    return img
  })

  // init canvas context
  const canvas = heroCanvas.value
  ctx = canvas.getContext('2d')

  // initial draw & resize listener
  window.addEventListener('resize', resizeCanvas)
  images.forEach((img) => (img.onload = resizeCanvas))

  // start the 5s slideshow
  intervalId = setInterval(startSlide, 5000)
})

onBeforeUnmount(() => {
  clearInterval(intervalId)
  cancelAnimationFrame(rafId)
  window.removeEventListener('resize', resizeCanvas)
})
</script>

<style scoped>
/* Import DIN Condensed */
@font-face {
  font-family: 'DIN Condensed';
  src: url('@/assets/fonts/DINCondensed.woff2') format('woff2'),
       url('@/assets/fonts/DINCondensed.woff') format('woff');
  font-weight: normal;
  font-style: normal;
}

/* Full viewport, no scrolling, light gray background */
.landing-page {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  margin: 0;
  
}

/* Left: text overlay */
.landing-page__content {
  position: absolute;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  z-index: 2;
  background-color: #fff; /* prevent slideshow showing through */
}

/* Right: canvas slideshow */
.landing-page__hero {
  position: absolute;
  top: 0;
  left: 50%;
  width: 50%;
  height: 100%;
  z-index: 1;
  overflow: hidden;
}
.landing-page__canvas {
  width: 100%;
  height: 100%;
  display: block; /* remove inline gap */
}

/* Text positioning & underline animation */
.landing-page__link {
  font-family: 'DIN Condensed', sans-serif;
  position: absolute;
  line-height: 1;
  text-decoration: none;
  color: #111;
  text-transform: uppercase;
  margin: 0;
  overflow: visible;
}

/* Slide‐in underline */
.landing-page__link::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -4px;       /* tweak to sit just under text */
  width: 0;
  height: 5px;
  background: #111;   /* match your text color */
}

.landing-page__link:hover::after {
  width: 100%;
  cursor: pointer;
}

/* Individual link/title positioning */
.landing-page__link--title {
  top: 60px;
  left: 85px;
  font-size: clamp(2rem, 6vw, 60px);
}
.landing-page__link--portfolio {
  top: 200px;
  left: 85px;
  font-size: clamp(2rem, 10vw, 130px);
}
.landing-page__link--me {
  top: 350px;
  left: 85px;
  font-size: clamp(2rem, 10vw, 130px);
}
.landing-page__link--about {
  top: 500px;
  left: 85px;
  font-size: clamp(2rem, 10vw, 130px);
}
.landing-page__link--contact {
  top: 650px;
  left: 85px;
  font-size: clamp(2rem, 10vw, 130px);
}

/* Stack on mobile */
@media (max-width: 768px) {
  .landing-page__content,
  .landing-page__hero {
    position: static;
    width: 100%;
    height: auto;
  }
  .landing-page__content {
    padding: 2rem;
    background: #fff;
  }
  .landing-page__link {
    position: static;
    font-family: 'DIN Condensed', sans-serif;
    font-size: 2.5rem;
    display: block;
    margin: 0.5em 0;
  }
}
</style>
