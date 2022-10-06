<!-- 根据动态路由匹配参数后，生成对应的html填进template中 -->
<template>
    <button @click="b">123213</button>
    <div contenteditable="true" style="outline:none">
        <span>123</span>
        <span>123</span>
        <span>123</span>
        <div>12312

        </div>
    </div>
</template>

<script setup lang="ts">
import { Ref, ref } from 'vue';
// import {markdown} from 'markdown'
    const a = ref("")
    let nowElement : HTMLElement
    function b (){
    // let out = markdown.toHTML(a.value)
    let preModifyText:string
    let ModifyText:string
    
        
    }
    window.addEventListener("DOMCharacterDataModified",(e)=>{
        if(e instanceof MutationEvent)
        let a:HTMLElement = e.target as HTMLElement
        nowElement = a.parentElement as HTMLElement
        preModifyText = e. as string
    })

    window.addEventListener("keypress",(e)=>{
        
        if(e.key == " "){
            
            console.log();
            
        }
    })
    
    // console.log( markdown.toHTML( "Hello" ) );
</script>

<style scoped lang="scss">

</style>