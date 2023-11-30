<template>
  <div class="step">
    <div class="ring onstep compleated">1</div>
    <div class="bar">
      <span class="progress"></span>
    </div>
    <div class="ring">2</div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.step {
  display: flex;
  align-items: center;
  gap: 8px;
}
.ring {
  display: flex;
  width: 24px;
  height: 24px;
  padding: 10px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;

  color: var(--grey-300, #d0d5dd);
  font-family: Inter;
  font-size: 12px;
  font-style: normal;
  font-weight: 600;
  line-height: 18px; /* 150% */

  border-radius: 24px;
  border: 1px solid var(--grey-300, #d0d5dd);
}

.compleated {
  color: var(--success-500-base, #099137);
  border: 1px solid var(--success-500-base, #099137);
}

.bar {
  position: relative;
  width: 90px;
  height: 2px;
  border-radius: 2px;
  background: var(--success-50, #e7f6ec);
}

.progress {
  position: absolute;
  width: 50%;
  height: 100%;
  border-radius: 2px;
  background: var(--success-500-base, #099137);
}

.compleated,
.compleated ~ .bar {
  animation: scaleAnimation 0.3s forwards;
}

@keyframes scaleAnimation {
  0% {
    transform: scale(0.8);
  }
  50% {
    transform: scale(1.1);
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}
</style>