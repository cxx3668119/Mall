<template>
  <div>
    <nav-header></nav-header>
    <router-view></router-view>
    <nav-footer></nav-footer>
  </div>
</template>

<script>
// alert(`本网站个人精力有限 制作不完全完整
// 注册接口的问题 目前没有注册功能
// 登录账号admin1 密码admin1
// 轮播图123可以到产品详情。
// 大多数据都是通过后台接口交互获取
// 部分是静态。`);
import NavHeader from "./../components/NavHeader";
import NavFooter from "./../components/NavFooter";
export default {
  name: "nav-home",
  components: {
    NavHeader,
    NavFooter,
  },
};
</script>

<style>
</style>