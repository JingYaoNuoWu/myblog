<template>
    <h1 class="dynamic-title">{{ dynamicTitle }}</h1>
    <div id="tagContainer">
        <div id="tags">
            <div class="tag" v-for="item in 100" :key="item">{{item}}</div>
        </div>
        <!-- {{ contents }} -->
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

    const dynamicTitle = ref('标签');
    const contents = ref('内容');
</script>

<style scoped lang="scss">
    #tagContainer{
        display: flex;

    }
    .dynamic-title{
        text-align: left;
        font-size: 1.8rem;
        font-family: 'Lato', 'Microsoft Yahei', sans-serif;
        font-weight: 400;
    }
    #tags{
        width: 100%;
        display: flex;
        flex-wrap: wrap;
    }
    .tag{
        min-width: 6rem;
        min-height: 2.4rem;
        margin: .4rem .2rem;
        background-color: #76d1fc;
        border-radius: 10px;
        line-height: 2.4rem;
        cursor:pointer;
    }
    .tag:hover{
        background-color: #51849c ;
    }
</style>