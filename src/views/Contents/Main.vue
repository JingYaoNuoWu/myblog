<!-- 根据动态路由匹配参数后，生成对应的html填进template中 -->
<template>
    <el-input v-model="title" placeholder="请输入标题" />
    <div class="mg-top-bottom-10"></div>
    <div style="text-align: left;">
        <el-tag v-for="tag in dynamicTags" :key="tag" class="mx-1" closable :disable-transitions="false"
            @close="handleClose(tag)">
            {{ tag }}
        </el-tag>
        <el-autocomplete v-if="inputVisible" ref="InputRef" class="h-24 w-82" v-model="inputValue"
            :fetch-suggestions="querySearch" clearable @blur="handleInputConfirm" @keyup.enter="handleInputConfirm"
            placeholder="Please Input" />
        <el-button v-else class="button-new-tag ml-1" size="small" @click="showInput">
            + New Tag
        </el-button>
    </div>

    <el-input v-model="content" autosize type="textarea" placeholder="请输入内容" @input="consoleLogContent" />
</template>

<script setup lang="ts">
import { nextTick, onMounted, ref } from 'vue'
import { ElAutocomplete } from 'element-plus'
interface RestaurantItem {
    value: string
    link: string
}

const state1 = ref('')
const title = ref()
const content = ref()
const inputValue = ref('')
const dynamicTags = ref(['Tag 1', 'Tag 2', 'Tag 3'])
const inputVisible = ref(false)
const InputRef = ref<InstanceType<typeof ElAutocomplete>>()
const restaurants = ref<RestaurantItem[]>([])
function consoleLogContent() {
    console.log(content.value);
}


const handleClose = (tag: string) => {
    dynamicTags.value.splice(dynamicTags.value.indexOf(tag), 1)
}

const showInput = () => {
    inputVisible.value = true
    nextTick(() => {
        console.log(InputRef.value);

        InputRef.value!.focus()
    })
}

const handleInputConfirm = () => {
    if (inputValue.value) {
        dynamicTags.value.push(inputValue.value)
    }
    inputVisible.value = true
    inputValue.value = ''
}

const querySearch = (queryString: string, cb: any) => {
    const results = queryString
        ? restaurants.value.filter(createFilter(queryString))
        : restaurants.value
    // call callback function to return suggestions
    cb(results)
}
const createFilter = (queryString: string) => {
    return (restaurant: RestaurantItem) => {
        return (
            restaurant.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0
        )
    }
}
const loadAll = () => {
    return [
        { value: 'vue', link: 'https://github.com/vuejs/vue' },
        { value: 'element', link: 'https://github.com/ElemeFE/element' },
        { value: 'cooking', link: 'https://github.com/ElemeFE/cooking' },
        { value: 'mint-ui', link: 'https://github.com/ElemeFE/mint-ui' },
        { value: 'vuex', link: 'https://github.com/vuejs/vuex' },
        { value: 'vue-router', link: 'https://github.com/vuejs/vue-router' },
        { value: 'babel', link: 'https://github.com/babel/babel' },
    ]
}
onMounted(() => {
    restaurants.value = loadAll()
})
</script>

<style scoped lang="scss">
.inline-flex {
    display: inline-flex;
}

</style>
<style>
    
.w-82 {
    width: 82px;
}
.h-24{
    height: 24px;
}
</style>