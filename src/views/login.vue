<template>
  <div class="login">
    <h1>管理系统</h1>
    <el-form
      :model="ruleForm"
      :rules="rules"
      ref="ruleForm"
      label-width="100px"
      class="demo-ruleForm"
    >
      <el-form-item label="用户名" prop="name">
        <el-input v-model="ruleForm.name"></el-input>
      </el-form-item>
      <el-form-item label="密 码" prop="password">
        <el-input type="password" v-model="ruleForm.password"></el-input>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="login">登录</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>
<script>
export default {
  name: "login",
  data() {
    return {
      ruleForm: {
        name: "",
        password: "",
      },
      rules: {
        name: [
          { required: true, message: "请输入用户名", trigger: "blur" },
          {
            min: 4,
            max: 16,
            message: "长度在 4 到 16 个字符",
            trigger: "blur",
          },
        ],
        password: [
          { required: true, message: "请输入密码", trigger: "blur" },
          {
            min: 4,
            max: 16,
            message: "长度在 4 到 16 个字符",
            trigger: "blur",
          },
        ],
      },
    };
  },
  methods: {
    login: function () {
      let { name, password } = this.ruleForm;
      this.$http({
        method: "post",
        url: "/vue/loginP",
        data: {
          userName: name,
          password: password,
        },
      }).then((res) => {
        console.log(res.data.data.code);

        let { code } = res.data.data;
        if (code == "1") {
          sessionStorage.setItem("username", name); //setItem把数据存储到sessionStorage
          this.$router.push("/home");
        }
      });
    },
  },
};
</script>
