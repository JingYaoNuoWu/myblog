<template>
    <div class="container">
        <div class="main-content">
            <ContentBox :contentList="[
                {id:1,title:'haha',content:'123',time:'22'},
                {id:1,title:'23123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'haha',content:'123',time:'22'},
                {id:1,title:'23123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'haha',content:'123',time:'22'},
                {id:1,title:'23123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'haha',content:'123',time:'22'},
                {id:1,title:'23123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'},
                {id:1,title:'123',content:'123',time:'22'}
            ]">
                
            </ContentBox>
        </div>
        <div class="aside-tips"></div>
    </div>
</template>
<script setup lang="ts">
import ContentBox from '@/components/mycomponents/ContentBox.vue';
// import TestDiv from '@/components/mycomponents/TestDiv.vue';

</script>

<style scoped lang="scss">
.container {
    display: flex;

    .main-content {
        flex-basis: 70%;
        padding: 0 20px;
    }
}

</style>