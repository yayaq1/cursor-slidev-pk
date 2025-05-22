<template>
  <!-- Wrapper fills the entire slide canvas -->
  <div class="glow-wrapper w-full h-full relative">
    <!-- Gradient layer fills wrapper -->
    <div class="glow-bg" aria-hidden="true"></div>

    <!-- Centered content -->
    <div class="relative z-10 flex items-center justify-center h-full">
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
// No additional logic needed
</script>

<style scoped>
.glow-wrapper {
  position: relative;
  width: 100%;
  height: 100%; /* respect slide canvas height */
  overflow: hidden;
}

.glow-bg {
  position: absolute;
  inset: 0;
  pointer-events: none;
  overflow: hidden;
}

.glow-bg::before {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  width: 200vmax;
  height: 200vmax;
  transform: translate(-50%, -50%);
  background: conic-gradient(from 0deg, #ff0080, #ff8c00, #40e0d0, #ff0080);
  filter: blur(150px) saturate(1.2);
  opacity: 0.5;
  animation: subtleGlow 45s ease-in-out infinite alternate;
}

@keyframes subtleGlow {
  0% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.4;
  }
  50% {
    transform: translate(-52%, -48%) scale(1.05);
    opacity: 0.6;
  }
  100% {
    transform: translate(-50%, -50%) scale(1);
    opacity: 0.4;
  }
}
</style> 