<template>
  <button class="button">
    <slot></slot>
  </button>
</template>

<script setup>
import {defineComponent} from "vue";

const buttonComponent = defineComponent({
  name: "button-component",
})
</script>

<style scoped>
.button {
  text-align: center;
  width: 100%;
  padding: 1rem 1.5rem;
  border: none;
  border-radius: .625rem;
  font-size: 1.25rem;
  font-weight: 400;
  color: #FAFAFA;
  background: linear-gradient(90deg, #D7650F 0%, #E1250A 100%);
  transition: 250ms ease-out all;
}

.button[aria-disabled="true"] {
  background: linear-gradient(90deg, #8A8A8A 0%, #505050 100%);
  color: #FAFAFA;
}

.button:not([aria-disabled]):hover {
  box-shadow: 0 .5rem 1.5rem rgba(215, 101, 15, 0.7);
  border-radius: 2.5rem;
}
</style>
