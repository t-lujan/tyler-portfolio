<template>
  <div class="home">
    <!-- Disable canvas on mobile -->
    <canvas
      v-if="!isMobile"
      ref="pongCanvas"
      class="pong-bg"
    ></canvas>

    <div class="about">
      <p>
        I’m a junior dev focused on crafting clean, efficient, and interactive web experiences.
        My passion is building thoughtful UI/UX with Vue.js, JavaScript, and modern front-end tools. Google Ads Search Certified.
        I’m constantly learning and exploring new technologies to improve my skills. 
        When I’m not coding, I enjoy hanging out with my wife and my 1 year old daughter, playing games, and playing golf.
      </p>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const pongCanvas = ref(null)
let ctx

const isMobile = /Mobi|Android|iPhone|iPad/i.test(navigator.userAgent) // better mobile detection

const paddle = {
  width: 10,
  height: 80,
  leftY: 0,
  rightY: 0,
  speed: 4
}

const ball = {
  x: 0,
  y: 0,
  radius: 6,
  vx: 3,
  vy: 2
}

let rightX = 0

const resizeCanvas = () => {
  const canvas = pongCanvas.value
  if (!canvas) return
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight

  paddle.leftY = canvas.height / 2 - paddle.height / 2
  paddle.rightY = canvas.height / 2 - paddle.height / 2

  rightX = canvas.width - paddle.width - 10
  resetBall(canvas)
}

const resetBall = (canvas) => {
  ball.x = canvas.width / 2
  ball.y = canvas.height / 2
  ball.vx = 3 * (Math.random() > 0.5 ? 1 : -1)
  ball.vy = 2 * (Math.random() > 0.5 ? 1 : -1)
}

const handleMouseMove = (e) => {
  const bounds = pongCanvas.value.getBoundingClientRect()
  const x = e.clientX - bounds.left
  if (x < bounds.width / 2) {
    paddle.leftY = e.clientY - bounds.top - paddle.height / 2
  }
}

const draw = () => {
  const canvas = pongCanvas.value
  ctx.clearRect(0, 0, canvas.width, canvas.height)

  const isDark = document.body.classList.contains('dark')
  const color = isDark ? 'white' : 'black'

  ball.x += ball.vx
  ball.y += ball.vy

  if (ball.y - ball.radius <= 0 || ball.y + ball.radius >= canvas.height) {
    ball.vy *= -1
  }

  if (
    ball.x - ball.radius <= 10 + paddle.width &&
    ball.y >= paddle.leftY &&
    ball.y <= paddle.leftY + paddle.height
  ) {
    ball.vx *= -1
  }

  if (
    ball.x + ball.radius >= rightX &&
    ball.y >= paddle.rightY &&
    ball.y <= paddle.rightY + paddle.height
  ) {
    ball.vx *= -1
  }

  if (ball.x < 0 || ball.x > canvas.width) {
    resetBall(canvas)
  }

  const aiCenter = paddle.rightY + paddle.height / 2
  if (ball.y < aiCenter - 10) paddle.rightY -= paddle.speed
  if (ball.y > aiCenter + 10) paddle.rightY += paddle.speed
  paddle.rightY = Math.max(0, Math.min(canvas.height - paddle.height, paddle.rightY))

  ctx.fillStyle = color
  ctx.beginPath()
  ctx.arc(ball.x, ball.y, ball.radius, 0, Math.PI * 2)
  ctx.fill()

  ctx.fillRect(10, paddle.leftY, paddle.width, paddle.height)
  ctx.fillRect(rightX, paddle.rightY, paddle.width, paddle.height)
}

const animate = () => {
  draw()
  requestAnimationFrame(animate)
}

onMounted(() => {
  if (isMobile) return // ✅ HARD SKIP PONG INIT
  const canvas = pongCanvas.value
  ctx = canvas.getContext('2d')
  resizeCanvas()
  animate()
  window.addEventListener('resize', resizeCanvas)
  window.addEventListener('mousemove', handleMouseMove)
})
</script>

<style scoped>
.home {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  font-family: 'Inter', sans-serif;
  box-sizing: border-box;
}

.about {
  position: absolute;
  right: 3rem;
  bottom: 3rem;
  max-width: 300px;
  font-size: 0.9rem;
  text-align: right;
  z-index: 2;
  line-height: 1.5;
}

/* 🔧 Mobile-specific fix */
@media (max-width: 768px) {
  .about {
    position: absolute;
    bottom: 1.5rem;
    right: 1.5rem;
    left: 1.5rem;
    text-align: right;
    max-width: unset;
    font-size: 0.95rem;
    padding: 0;
    line-height: 1.5;
    z-index: 2;
  }
}

.pong-bg {
  position: fixed;
  inset: 0;
  z-index: 0;
  width: 100%;
  height: 100%;
  background: radial-gradient(circle, #ccc 0%, transparent 100%);
  pointer-events: none;
}
</style>
