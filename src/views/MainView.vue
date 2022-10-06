<template>
  <div class="common-layout">
    <el-header :style="{top: topBarHideFlag?'-60px':0 }"></el-header>
    <div></div>
    <el-container>
      <el-aside id="side-bar">
        <!-- 这是侧边栏 ， 顶部是头像， 下面是姓名和座右铭，然后是四个菜单 -->
        <!-- 外层直接flex布局吧 -->
        <div id="aside-wapper">
          <div class="avatar-container">
            <el-avatar :size="50" src="https://cube.elemecdn.com/e/fd/0fc7d20532fdaf769a25683617711png.png">
              <img  src="@/assets/logo.png" />
            </el-avatar>
          </div>
          <ul class="main-menu">
            <li :class="{active:nowIndex==0}" @click="changeNav('/',0)">
              <h2>主页</h2>
            </li>
            <li :class="{active:nowIndex==1}" @click="changeNav('/tags',1)">
              <h2>标签</h2>

            </li>
            <li :class="{active:nowIndex==2}" @click="changeNav('/class',2)">
              <h2>分类</h2>

            </li>
            <li :class="{active:nowIndex==3}" @click="changeNav('/archives',3)">
              <h2>归档</h2>

            </li>
          </ul>

        </div>
      </el-aside>

      <el-container>
        <el-main ref="dom">
          <div class="main-wapper">
            <!-- //内容部分 -->
            <div class="main-inner-wapper">
              <div class="main-content">
                <router-view />

              </div>
              <div class="aside-tips">
                <div class="aside-tips-item ">
                  <h1>最近更新</h1>
                  <ul>
                    <li>
                      <a href="#">123</a>
                    </li>
                    <li><a href="#">123</a></li>
                    <li><a href="#">123</a></li>
                  </ul>

                </div>
                <div class="aside-tips-item">
                  <h1>热点标签</h1>
                  <ul>
                    <li>
                      <a href="#">123</a>
                    </li>
                    <li><a href="#">123</a></li>
                    <li><a href="#">123</a></li>
                  </ul>
                </div>
                <div id="article-content" :class="{'aside-tips-item':true,'tips-topbar-down':!topBarHideFlag}">
                  <h1>文章目录</h1>
                  <ul>
                    <li>
                      <a href="#">123</a>
                    </li>
                    <li><a href="#">123</a></li>
                    <li><a href="#">123</a></li>
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
import { onUnmounted, reactive, Ref, ref, watch } from "vue";
import { onMounted } from "vue";
import { useRouter } from "vue-router";

const topBarHideFlag = ref(false);

const dom: Ref = ref(null);

let scrollTop: any = 0

const router = useRouter()

const nowIndex = ref(0)
let topBarInterval: any
onMounted(() => {
  topBarInterval = setInterval(() => {
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
onUnmounted(() => {
  console.log("onUnmounted");

  clearInterval(topBarInterval)
})

function changeNav(path: string, index: number) {
  router.push(path)
  nowIndex.value = index
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
    display: flex;

    .main-content {
      flex-basis: 70%;
      padding: 0 2rem !important;
    }
  }
}


.el-container .el-aside {
  width: 260px;
  background-color: #876;
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

.main-menu {
  padding: 0;
  margin-top: 40px;

  li {
    list-style: none;
    margin: 40px 0;
    height: 3.3rem;
    display: flex;
    justify-content: center;
    margin: 0;
    align-items: center;
    cursor: pointer;
    color: #ffffff79;
    h2{
      width: 100%;
      margin: 0;
    }
  }

  // li:nth-child(1).active {
  //     top: -10px
  // }
  li:last-child::after {
    width: 3px;
    background-color: red;
    height: 2rem;
    content: "";
    position: relative;
    top: 0px;
    display: block;
    box-sizing: border-box;
    transition: top .5s ease;
    visibility: hidden;
  }
  li.active:nth-child(1)~li:last-child::after{
    top: -9.9rem ;
    visibility :visible;
  }
  li:nth-child(1):hover~li:last-child::after {
    top: -9.9rem !important;
    visibility :visible !important;
  }

  li.active:nth-child(2)~li:last-child::after{
    top: -6.6rem ;
    visibility: visible ;
  }
  li:nth-child(2):hover~li:last-child::after {
    top: -6.6rem !important;
    visibility: visible !important;
  }
  li.active:nth-child(3)~li:last-child::after{
    top: -3.3rem ;
    visibility: visible ;
  }
  li:nth-child(3):hover~li:last-child::after {
    top: -3.3rem !important;
    visibility: visible !important;
  }
  li.active:nth-child(4)::after{
    top: 0px ;
    visibility: visible;
  }
  li:nth-child(4):hover::after {
    top: 0px !important;
    visibility: visible !important;
  }

}
.avatar-container img{
  transition: all .5s ease;

}
.avatar-container span:hover img{
  transform: scale(1.1,1.1);
}

.aside-tips{
  display: flex;
  flex-direction: column;
  // .aside-tips-item{
  // }
  #article-content{
    transition: top .4s ease;
    position:sticky;
    top:3rem;
  }
}
.tips-topbar-down{
  top:calc(3rem + 60px) !important;
}
</style>