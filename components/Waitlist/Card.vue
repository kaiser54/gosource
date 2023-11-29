<template>
  <div
    class="flex border select-card"
    :class="{ selected: selectedItem === data.value }"
    @mouseover="handleMouseOver"
    @mouseleave="handleMouseLeave"
    @click="$emit('selectEvent', data.value)"
  >
    <div class="img-select flex">
      <img :src="data.img" alt="" />
      <div class="radio">
        <CheckBox :isHovered="isHovered" />
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

const isHovered = ref(false);
const handleMouseOver = () => {
  isHovered.value = true;
};

const handleMouseLeave = () => {
  isHovered.value = false;
};

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

.select-card:hover,
.select-card:hover svg circle {
  border: 1px solid var(--grey-300, #d0d5dd);
  stroke: var(--grey-300, #d0d5dd);
  opacity: 1;
}

.img-select {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  align-self: stretch;
}

.selected {
  border: 1px solid var(--orange-orange-300, #ee806a);
  background: var(--orange-orange-25, #fdf5f4);
}

.selected:hover {
  border: 1px solid var(--orange-orange-300, #ee806a);
}

</style>