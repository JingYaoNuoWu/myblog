<template>
  <div class="common-layout">
      <el-header>Header</el-header>
      <div style=""></div>

    <el-container>
      <el-aside id="side-bar" width="200px">
        <div id="aside-wapper">
          <div style="background-color: #000000ff;height: 100vh;"></div>
        </div>
      </el-aside>

      <el-container>
        <el-main>
          <div class="main-wapper">
            <div style="height:1000px">
              <div v-for="item in 10" :key="item">123</div>
            </div>
          </div>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "@vue/reactivity";

let a = ref(1);
</script>

<style>
.el-container{
  height: 100%;
}
.main-wapper {
  box-sizing: border-box;
  min-height: 100vh;
  padding-top: 60px;
}
.el-container .el-aside {
  width: 260px;
}
.el-container .el-main {
  padding: 0;
  padding-left: calc((100% - 1100px)/2);
}
.el-header {
  position: fixed;
  top:0;
  right: 0;
  left: 260px;
  min-width: 100vh;
  box-shadow: 0px 3px 5px 0 rgba(0, 0, 0, 0.05);
  z-index: 99999;
}

#side-bar{
  height: 100%; 
}
#aside-wapper{
  width: 100%;
  overflow-y: auto;

}
</style>