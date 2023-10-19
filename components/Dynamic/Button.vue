<template>
  <button
    @click="emitFunction"
    class="button"
    :class="buttonClasses"
    :disabled="disabled"
  >
    <div class="" v-if="showText">{{ buttonText }}</div>
    <slot name="svg"></slot>
  </button>
</template>
  
  <script>
export default {
  props: {
    buttonText: {
      type: String,
      required: true,
    },
    size: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
    },
    showText: {
      type: Boolean,
      default: true,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    buttonClasses() {
      return {

        // Button size

        micro: this.size === "text-button-micro micro",
        small: this.size === "text-button-small small",
        medium: this.size === "text-button-medium medium",
        large: this.size === "text-button-large large",

        // Button type

        primary: this.type === "primary",
        secondary: this.type === "secondary",
        "neutral-outline": this.type === "neutral-outline",
        "neutral-filled": this.type === "neutral-filled",
        destructive: this.type === "destructive",
        "link-primary": this.type === "link-primary",
        "link-neutral": this.type === "link-neutral",

        // icon position

        "icon-left": this.icon === "icon-left",
        "icon-right": this.icon === "icon-right",
        "icon-button": this.showText === false,
      };
    },
  },
  methods: {
    emitFunction() {
      this.$emit("clickButton");
    },
  },
};
</script>