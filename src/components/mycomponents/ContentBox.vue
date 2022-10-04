<template>
    <TestDiv :params="['100%','auto','blue']">
        <TestDiv class="content-item" :key="item.id" v-for="item in contentList" :params="['100%','200px','red']">
            <TestDiv class="content-item-item" :params="['100%','auto','red']">
                <h1>
                    {{ item.title }}
                </h1>
            </TestDiv>
            <TestDiv class="content-item-item" :params="['100%','auto','red']">
                <p>
                    {{ item.content}}

                </p>
            </TestDiv>
            <TestDiv class="content-item-item" :params="['100%','auto','red']">
                <p>
                    {{ item.time}}
                </p>
            </TestDiv>
        </TestDiv>
    </TestDiv>
</template>
  
<script setup lang="ts" >
import TestDiv from './TestDiv.vue';
// const props = defineProps(["width","height","backgroundColor"]);
interface contentlist {
    [index:number]:contentObj
}
interface contentObj {
    id:number,
    title:string,
    content:string,
    time:string
}
defineProps<{
    contentList: contentlist
}>()
</script>
  
<style lang="scss">

.content-item {
    margin-top: 10px;
    display: flex;
    flex-direction: column;
    text-align: left;
    
}

.content-item:first-child {
    margin-top: 0;
}
.content-item-item:nth-child(1),.content-item-item:nth-child(3){
    flex-basis:30%;
    padding: 10px;
    box-sizing: border-box;
    }
.content-item-item:nth-child(2){
    flex-basis:50%;
    padding: 10px;
    box-sizing: border-box;
}
// .content-item-item:nth-child(3){
//     flex-basis:20%;
//     padding: 10px;
//     box-sizing: border-box;
// }
</style>