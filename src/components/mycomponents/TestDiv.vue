<template>
  <div :style="{ width: width + 'px', height : height + 'px' ,backgroundColor: backgroundColor}">
    <slot></slot>
  </div>
  
</template>

<script setup lang="ts" >
// const props = defineProps(["width","height","backgroundColor"]);
defineProps<{
  width?: string
  height?: string
  backgroundColor?:string
}>()
</script>

<style>
</style>