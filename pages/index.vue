<template>
  <div>
    <DynamicInput v-model="firstName" type="number" class="inputmee" />
    <DynamicButtonNav
      class="nav-button"
      buttonText="click me"
      url="/"
      :isLoading="true"
    />
    <DynamicButtonMain
      class="nav-button"
      buttonText="click me"
      size="large"
      type="primary"
      :isLoading="true"
    />
    <div class="container">
      <input type="checkbox" id="input-1" class="check-input" />
      <label for="input-1" class="checkbox">
        <svg viewBox="0 0 22 16" fill="none">
          <path d="M1 6.85L8.09677 14L21 1" />
        </svg>
      </label>
      <span>HTML</span>
    </div>
    <WaitlistCard
      v-for="(data, index) in waitlistData"
      :key="index"
      :data="data"
      :selectedItem="selectedItem"
      @selectEvent="selectEvent($event)"
    />
    <DynamicButtonNav buttonText="click me please" url="" />
    <p>{{ firstName }}</p>
    <Account name="Agboola t." />
  </div>
</template>

<script setup>
import { ref } from "vue";

const firstName = ref("");

const waitlistData = ref([
  {
    title: "GoSource for Business",
    snippet:
      "Get access to buy on credit, instant invoice, fast payments and 24hours delivery",
    value: "business",
    img: "/images/business.png",
  },
  {
    title: "GoSource for Individual",
    snippet:
      "Buy your food items with discounts, lesser prices and get them in 24hours",
    value: "individual",
    img: "/images/individual.png",
  },
]);

const selectedItem = ref("");
const selectEvent = (e) => {
  selectedItem.value = e;
};
</script>

<style scoped>
.container {
  padding: 20px;
  background-color: antiquewhite;
  margin: 1rem 0;
  display: flex;
  align-items: center;
}
.container span {
  margin-left: 1rem;
}
.check-input {
  display: none;
}
.checkbox {
  width: 25px;
  height: 25px;
  border: 2px solid #fff;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  padding: 3px;
  transition: 0.3s all;
}
.checkbox svg {
  width: 20px;
  height: 20px;
}
.check-input:checked + .checkbox {
  background: #26bfbf;
  border: 2px solid #26bfbf;
}
.check-input:checked + .checkbox svg path {
  stroke-dasharray: 500;
  stroke-dashoffset: 500;
  stroke: #fff;
  stroke-width: 3;
  animation: check 4s forwards;
}
.checkbox::before {
  content: "";
  background: #26bfbf66;
  position: absolute;
  border-radius: 50%;
  transform: scale(0);
  display: block;
  width: 60px;
  height: 60px;
  z-index: -1;
}
.check-input:checked + .checkbox::before {
  animation: ripple 0.3s;
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
</style>
