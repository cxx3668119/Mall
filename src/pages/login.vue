<template>
  <div class="login">
    <div class="wrapper">
      <!-- 粒子 -->
      <vue-particles
        class="particles"
        color="#fff"
        :particleOpacity="0.7"
        :particlesNumber="60"
        shapeType="circle"
        :particleSize="4"
        linesColor="#fff"
        :linesWidth="1"
        :lineLinked="true"
        :lineOpacity="0.4"
        :linesDistance="150"
        :moveSpeed="2"
        :hoverEffect="true"
        hoverMode="grab"
        :clickEffect="true"
        clickMode="push"
      >
      </vue-particles>
      <div class="container">
        <div class="login-form">
          <h3>
            <span class="checked">帐号登录</span><span class="sep-line">|</span
            ><span>扫码登录</span>
          </h3>
          <div class="input">
            <input type="text" placeholder="请输入帐号" v-model="username" />
          </div>
          <div class="input">
            <input
              type="password"
              placeholder="请输入密码"
              v-model="password"
            />
          </div>
          <div class="btn-box">
            <a href="javascript:;" class="btn" @click="login">登录</a>
          </div>
          <div class="tips">
            <div class="sms" @click="register">手机短信登录/注册</div>
            <div class="reg">立即注册<span>|</span>忘记密码？</div>
          </div>
        </div>
      </div>
    </div>
    <!-- <div class="footer">
      <div class="footer-link">
        <a href="/#/index" target="_blank">小米商城</a><span>|</span>
        <a href="https://github.com/cxx3668119" target="_blank">我的Github</a><span>|</span>
        <a href="https://juejin.cn/user/1688471139790455" target="_blank">我的博客</a><span></span>
      </div>
      <p class="copyright">
        Copyright ©2021
        最终解释权归陈新昕所有
      </p> -->
  </div>

  <!-- </div> -->
</template>
<script>
import { mapActions } from "vuex";
export default {
  name: "login",
  data() {
    return {
      username: "",
      password: "",
      userId: "",
    };
  },
  methods: {
    login() {
      let { username, password } = this;
      this.axios
        .post("/api/user/login", {
          username,
          password,
        })
        .then((res) => {
          this.$cookie.set("userId", res.id, { expires: "Session" });
          this.$store.dispatch("saveUserName", res.username);
          this.saveUserName(res.username);
          this.$router.push({
            name: "index",
            params: {
              from: "login",
            },
          });
        });
    },
    ...mapActions(["saveUserName"]),
    register() {
      this.axios
        .post("/api/user/register", {
          username: "admin1",
          password: "admin1",
          email: "admin1@163.com",
        })
        .then(() => {
          this.$message.success("注册成功");
        });
    },
    lucency() {
      //视图透明度
      let loginFrom = document.querySelector(".login-form");
      loginFrom.style.opacity = 1.0;
    },
    unlucency() {
      //视图透明度
      let loginFrom = document.querySelector(".login-form");
      loginFrom.style.opacity = 0.5;
    },
  },
};
</script>
<style lang="scss">
.login {
  & > .container {
    height: 113px;
    img {
      width: auto;
      height: 100%;
    }
  }
  .particles {
    width: 100%;
    height: 100%;
    position: absolute;
  }
  .wrapper {
    background: url("/imgs/login-bg-2.jpg") no-repeat center / 100% 100%;
    width: 100vw;
    height: 100vh;
    position: relative;
    .container {
      height: 100%;
      .login-form {
        box-sizing: border-box;
        padding-left: 31px;
        padding-right: 31px;
        width: 410px;
        height: 510px;
        background-color: #ffffff;
        opacity: 0.85;
        bottom: 29px;
        right: 0;
        position: absolute;
        top: 150px;
        right: 0;
        left: 0;
        transform: scale(0.9);
        margin: auto;
        h3 {
          line-height: 23px;
          font-size: 24px;
          text-align: center;
          margin: 40px auto 49px;
          .checked {
            color: #ff6600;
          }
          .sep-line {
            margin: 0 32px;
          }
        }
        .input {
          display: inline-block;
          width: 348px;
          height: 50px;
          border: 1px solid #e5e5e5;
          margin-bottom: 20px;
          input {
            width: 100%;
            height: 100%;
            border: none;
            padding: 18px;
          }
        }
        .btn {
          width: 100%;
          line-height: 50px;
          margin-top: 10px;
          font-size: 16px;
        }
        .tips {
          margin-top: 14px;
          display: flex;
          justify-content: space-between;
          font-size: 14px;
          cursor: pointer;
          .sms {
            color: #ff6600;
          }
          .reg {
            color: #999999;
            span {
              margin: 0 7px;
            }
          }
        }
      }
    }
  }
  .footer {
    height: 100px;
    padding-top: 60px;
    color: #999999;
    font-size: 16px;
    text-align: center;
    .footer-link {
      a {
        color: #999999;
        display: inline-block;
      }
      span {
        margin: 0 10px;
      }
    }
    .copyright {
      margin-top: 13px;
    }
  }
}
</style>