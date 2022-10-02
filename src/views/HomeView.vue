<template>
  <div class="common-layout">
    <el-container>
      <el-aside width="200px">Aside</el-aside>
      <el-container>
        <el-main>

            <div class="main-wapper">
        <el-header>Header</el-header>

            </div></el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
  import { ref } from "@vue/reactivity";


  let a  = ref(1);

  

  
</script>

<style>
.main-wapper{
  min-height: 100vh;
}
</style>