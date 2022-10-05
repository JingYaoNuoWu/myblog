<template>
  <div :style="{ width: `${params[0]}`, height : `${params[1]}`,backgroundColor:`${params[2]}`}">
    <slot></slot>
  </div>
  
</template>

<script setup lang="ts" >
defineProps<{
  params:[string,string,string]
}>()


</script>

<style>
</style>