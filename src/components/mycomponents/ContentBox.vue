<template>
    <TestDiv :params="['100%','auto','blue']">
        <TestDiv class="content-item" :key="item.id" v-for="item in contentList" :params="['100%','200px','red']">
        </TestDiv>
    </TestDiv>
</template>
  
<script setup lang="ts" >
import TestDiv from './TestDiv.vue';
// const props = defineProps(["width","height","backgroundColor"]);
interface contentObj {
    id:number,
    title:string,
    content:string,
    time:string
}
defineProps<{
    contentList: contentObj [] 
}>()
</script>
  
<style>

.content-item {
    margin-top: 10px;
}

.content-item:first-child {
    margin-top: 0;
}
</style>