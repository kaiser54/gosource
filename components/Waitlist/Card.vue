<template>
  <div
    class="flex border select-card"
    @click="$emit('selectEvent', data.value)"
    :class="{ selected: selectedItem === data.value }"
  >
    <div class="img-select flex">
      <img :src="data.img" alt="" />
      <div class="radio">
        <svg viewBox="0 0 25 25" width="25" height="25">
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
      </div>
    </div>
    <div class="content-flex">
      <h4 class="heading-4-bold">{{ data.title }}</h4>
      <p class="body-small body-small-regular">{{ data.snippet }}</p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
const { data, selectedItem } = defineProps({
  data: {
    type: Object,
    required: true,
  },
  selectedItem: {
    type: String,
    required: true,
  },
});
</script>

<style>
.flex {
  display: flex;
}
h4 {
  color: var(--grey-700, #344054);

  /* H4/Heading 4 Bold */
  font-family: Graphik;
  font-size: 20px;
  font-style: normal;
  font-weight: 600;
  line-height: 30px; /* 150% */
  letter-spacing: -0.3px;
}
p {
  color: var(--grey-500, #667185);

  /* Body Small/Body Small Regular */
  font-family: Inter;
  font-size: 14px;
  font-style: normal;
  font-weight: 400;
  line-height: 21px; /* 150% */
  letter-spacing: -0.2px;
}
</style>

<style scoped>
.select-card {
  padding: 20px;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  gap: 24px;
  cursor: pointer;
  max-width: 237.5px;
  width: 100%;
  border-radius: 16px;
  border: 1px solid var(--grey-100, #f0f2f5);
  background: var(--White, #fff);

  transition: all 0.3s ease-out;
}

.select-card:hover {
  border: 1px solid var(--grey-300, #d0d5dd);
}

.img-select {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  align-self: stretch;
}
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
}

svg path {
  width: 100px;
  height: 100px;
  transform: translate(-50%, -50%);
  position: absolute;
  top: 50%;
  left: 50%;
  transform-origin: center center;

  transition: opacity 0.3s, transform 0.3s;
  transform: scale(0.4);
  opacity: 1;
}

.selected {
  border: 1px solid var(--orange-orange-300, #ee806a);
  background: var(--orange-orange-25, #fdf5f4);
}

.selected:hover {
  border: 1px solid var(--orange-orange-300, #ee806a);
}

.selected svg path {
  opacity: 1;
  animation: scaleAnimation 0.3s forwards;
}
.selected svg circle {
  fill: #09420c;
  animation: scaleAnimation 0.3s forwards;
}

@keyframes scaleAnimation {
  0% {
    transform: scale(0.4);
  }
  50% {
    transform: scale(1.6);
  }
  100% {
    transform: scale(1);
    opacity: 1;
  }
}
</style>