<template>
  <svg
    :class="{ selected: clicked, onHover: isHovered }"
    viewBox="0 0 25 25"
    width="25"
    height="25"
  >
    <circle cx="12" cy="12" r="11" />
    <path
      d="M8.5,12l2.5,2.5L15.5,10"
      fill="none"
      stroke="#fff"
      stroke-width="2"
      stroke-linecap="round"
      stroke-linejoin="round"
    />
  </svg>
</template>

<script setup>
import { ref, computed } from "vue";
const { clicked, isHovered } = defineProps({
  clicked: {
    type: Boolean,
    default: false,
  },
  isHovered: {
    type: Boolean,
    default: false,
  },
});
</script>

<style scoped>
svg {
  transition: opacity 0.3s, transform 0.3s;
}

svg circle {
  stroke: #e4e7ec;
  stroke-width: 1.66667px;
  fill: none;

  width: 100px;
  height: 100px;
  border-radius: 50%;
  opacity: 0.5;

  /* transform-origin: center center; */
  transition: all 0.3s ease-out;
}

svg path {
  width: 100px;
  height: 100px;
  /* transform: translate(-50%, -50%);
  position: absolute;
  top: 50%;
  left: 50%;
  transform-origin: center center; */

  transition: opacity 0.3s, transform 0.3s;
  /* transform: scale(0.4); */
  opacity: 1;
}

.selected path {
  stroke-dasharray: 500;
  stroke-dashoffset: 500;
  animation: check 4s forwards;
}

svg.onHover circle {
  border: 1px solid var(--grey-300, #d0d5dd);
  stroke: var(--grey-300, #d0d5dd);
  opacity: 1;
}

.selected svg path {
  opacity: 1;
  /* animation: scaleAnimation 0.3s forwards; */
}
.selected {
  opacity: 1;
  animation: scaleAnimation 0.3s forwards;
}
.selected svg circle {
  fill: #09420c;
  animation: scaleAnimation 0.3s forwards;
}

@keyframes check {
  to {
    stroke-dashoffset: 0;
  }
}
@keyframes ripple {
  to {
    transform: scale(1);
  }
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