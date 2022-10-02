<template>
  <div class="common-layout">
      <el-header>Header</el-header>

    <el-container>
      <el-aside id="side-bar" width="200px">
        <div id="aside-wapper">
          <div style="background-color: #000000ff;height: 100vh;"></div>
        </div>
      </el-aside>

      <el-container>
        <el-main>
          <div class="main-wapper">
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
.main-wapper {
  min-height: 100vh;
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
}
#side-bar{
  max-height: 100vh;
}
#aside-wapper{
  width: 100%;
  overflow-y: auto;

}
</style>