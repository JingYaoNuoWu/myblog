<template>
  <div class="common-layout">
    <el-header :style="{top: topBarHideFlag?'-60px':0 }"></el-header>
    <div></div>

    <el-container>
      <el-aside id="side-bar" width="200px">
        <div id="aside-wapper">
          <div style="background-color: #000000ff;height: 100vh;"></div>
        </div>
      </el-aside>

      <el-container>
        <el-main ref="dom" @scroll="scroll">
          <div class="main-wapper">
            <!-- //内容部分 -->
            <router-view/>
          </div>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
import { reactive, Ref, ref ,watch} from "vue";
import { onMounted } from "vue";

const topBarHideFlag = ref(false);

const dom: Ref = ref(null);


// onMounted(()=>{

// })
// watch(()=>dom.value.$el.scrollTop,(a)=>{    
//     console.log(a);
// })

function scroll() {
  if(dom.value.$el.scrollTop>60){
    topBarHideFlag.value = true
  }else{
    topBarHideFlag.value = false
  }
  

}


</script>

<style>
.el-container {
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
  top: 0;
  right: 0;
  left: 260px;
  min-width: 100vh;
  box-shadow: 0px 3px 5px 0 rgba(0, 0, 0, 0.05);
  z-index: 99999;
}

#side-bar {
  height: 100%;
}

#aside-wapper {
  width: 100%;
  overflow-y: auto;

}
</style>