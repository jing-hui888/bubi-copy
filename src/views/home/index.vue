<template>
  <div id="home">
    <!-- 左侧导航 -->
    <el-container>
      <Nav />
      <el-container>
        <!-- 头部 -->
        <el-header>
          <el-button class="butto" @click="goBack" type="primary"
            >退出按钮</el-button
          >
          <!-- 面包屑 -->
          <Mbx />
        </el-header>

        <!-- 主体部分 -->
        <el-main>Main</el-main>
        <!-- 页脚 -->
        <el-footer>Foote</el-footer>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import Nav from "./Nav";
import Mbx from "./Mbx.vue";
export default {
  name: "home",

  components: {
    Nav,
    Mbx,
  },
  methods: {
    goBack: function () {
      sessionStorage.removeItem("username"); //removeItem清除sessionStorage里面的数据
      this.$router.push("/login");
    },
  },
};
</script>

<style>
.el-header,
.el-footer {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 200px;
  height: 609px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 160px;
}

body > .el-container {
  margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
  line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
  line-height: 320px;
}
.butto {
  float: right;
  margin-top: 10px;
}
</style>