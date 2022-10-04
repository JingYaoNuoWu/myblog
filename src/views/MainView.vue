<template>
  <div class="common-layout">
    <el-header :style="{top: topBarHideFlag?'-60px':0 }"></el-header>
    <div></div>
    <el-container>
      <el-aside id="side-bar">
        <!-- 这是侧边栏 ， 顶部是头像， 下面是姓名和座右铭，然后是四个菜单 -->
        <!-- 外层直接flex布局吧 -->
        <div id="aside-wapper">
          <div class="avatar-container" @click="toPage('/')">
            <el-avatar :size="50" src="https://cube.elemecdn.com/e/fd/0fc7d20532fdaf769a25683617711png.png">
              <img src="@/assets/logo.png" />
            </el-avatar>
          </div>
          <ul>
            <li>
              <div @click="toPage('/tags')">
                <h2>1111</h2>
              </div>
            </li>
            <li>
              <div>
                <h2>2222</h2>

              </div>
            </li>
            <li>
              <div>
                <h2>3333</h2>

              </div>
            </li>

          </ul>

        </div>
      </el-aside>

      <el-container>
        <el-main ref="dom">
          <div class="main-wapper">
            <!-- //内容部分 -->
            <div class="main-inner-wapper">
              <router-view />

            </div>
          </div>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
import { reactive, Ref, ref, watch } from "vue";
import { onMounted } from "vue";
import ContentBox from "@/components/mycomponents/ContentBox.vue";
import { useRouter } from "vue-router";

const topBarHideFlag = ref(false);

const dom: Ref = ref(null);

let scrollTop: any = 0

const router = useRouter()

onMounted(() => {
  setInterval(() => {
    if (dom.value.$el.scrollTop > 60) {
      if (scrollTop < dom.value.$el.scrollTop) {
        topBarHideFlag.value = true

      } else if (scrollTop > dom.value.$el.scrollTop) {

        topBarHideFlag.value = false
      }
    } else {
      topBarHideFlag.value = false

    }

    scrollTop = dom.value.$el.scrollTop

  }, 300)
})

function toPage(path:string) {
   router.push(path)
} 
</script>

<style lang="scss">
.el-container {
  height: 100%;
}

.main-wapper {
  box-sizing: border-box;
  min-height: 100vh;
  padding-top: 60px;

  .main-inner-wapper {
    min-height: calc(100vh - 60px);
    box-sizing: border-box;
    padding: 20px 0;
  }
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
  z-index: 99;
  background-color: rgb(43, 25, 233);
  transition: .6s all ease;
}

#side-bar {
  height: 100%;
}

#aside-wapper {
  width: 100%;
  overflow-y: auto;
  display: flex;
  flex-direction: column;
}

.avatar-container {
  margin-top: 60px;
}
</style>