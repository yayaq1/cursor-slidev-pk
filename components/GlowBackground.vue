<template>
  <div class="glow-wrapper h-full w-full flex items-center justify-center">
    <!-- Gradient layer -->
    <div class="glow-bg" aria-hidden="true"></div>

    <!-- Slot content above the glow -->
    <div class="relative z-10">
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
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.glow-bg {
  position: absolute;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  pointer-events: none;
}

.glow-bg::before {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  width: 140vmax;
  height: 140vmax;
  transform: translate(-50%, -50%);
  background: conic-gradient(from 0deg, #ff0080, #ff8c00, #40e0d0, #ff0080);
  filter: blur(120px) saturate(1.6);
  opacity: 0.7;
  animation: spin 18s linear infinite;
}

@keyframes spin {
  from {
    transform: translate(-50%, -50%) rotate(0deg);
  }
  to {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}
</style> 