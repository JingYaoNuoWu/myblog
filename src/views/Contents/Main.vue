<!-- 根据动态路由匹配参数后，生成对应的html填进template中 -->
<template>
    <div ref="editableContent" contenteditable="true" style="outline:none">

        <div>12312

        </div>
    </div>
</template>

<script setup lang="ts">
import { logicalExpression } from '@babel/types';
import { onMounted, Ref, ref } from 'vue';
// import {markdown} from 'markdown'
const a = ref("")
let nowElement: MutationObserver
const editableContent: Ref = ref(null);
let isSpace = false;
let oldValue: any;
let newValue: any;
function modifyFn(a: any, b: any) {

    if (a instanceof Array && a.length == 1) {
        oldValue = a[0].oldValue
        newValue = a[0].target.nodeValue
        console.log(panduan(oldValue, newValue, a[0].target));

    }

    // for(let item of a){

    // }

}
function panduan(oldValue: string, newValue: string, ele: HTMLElement) {
    let oldValueFirstWord = oldValue.substring(0, 1)
    let oldValueSecondWord = oldValue.substring(1, 2)
    let newValueFirstWord = newValue.substring(0, 1)
    let newValueSecondWord = newValue.substring(1, 2)


    if (oldValueFirstWord != "#" || newValueFirstWord != "#") return false;

    // if(oldValueSecondWord == " ") return false;
    if (newValueSecondWord == " " && oldValueSecondWord != " " && isSpace) {

        let parentele = ele.parentElement
        if (parentele != null) {
            let text = parentele.innerText
            let dom = document.createElement("h1")
            dom.innerText = text

            dom.appendChild(document.createElement("br"))
            parentele.replaceWith(dom)
            // dom.setSelectionRange
        }
        return true;
    }
    return false;

}
onMounted(() => {
    const config = { characterData: true, characterDataOldValue: true, subtree: true };
    const observer = new MutationObserver(modifyFn)
    observer.observe(editableContent.value, config)



})

window.addEventListener("keypress", (e) => {
    if (e.key == " ") {
        isSpace = true
    }


})
window.addEventListener("keyup", (e) => {
    isSpace = false
})

    // console.log( markdown.toHTML( "Hello" ) );
</script>

<style scoped lang="scss">

</style>