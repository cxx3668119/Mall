<template>
  <div class="footer">
    <div class="footer-logo">
      <img src="/imgs/logo-footer.png" alt="" />
      <p>小米商城</p>
    </div>
    <div class="footer-link">
      <a href="https://privacy.mi.com/all/zh_CN/" target="_blank">
        小米集团隐私政策</a
      ><span>|</span>
      <a href="https://github.com/cxx3668119" target="_blank"> 我的github</a
      ><span>|</span>
      <a href="https://privacy.mi.com/all/zh_CN/" target="_blank">
        小米商城隐私政策</a
      ><span>|</span>
      <a href="https://www.mi.com/about/user-agreement" target="_blank">
        小米商城用户协议</a
      ><span>|</span>
      <a href="#">我的主页</a>
    </div>
    <div class="copyrigth">
      Copyright ©2020 <span class="mainweb">mi.futurefe.com</span> All Rights
      Reserved.
    </div>
  </div>
</template>

<script>
export default {
  name: "nav-footer",
};
</script>

<style lang='scss'>
.footer {
  height: 234px;
  border-top: 4px solid #ff6600;
  background-color: #333;
  color: #999;
  font-size: 16px;
  text-align: center;
  .footer-logo {
    margin-top: 46px;
    margin-bottom: 31px;
    img {
      width: 53px;
      height: 36px;
      margin-bottom: 13px;
    }
  }
  .footer-link {
    a {
      color: #999;
      display: inline-block;
    }
    span {
      margin: 0 10px;
    }
    margin-bottom: 13px;
  }
  .copyrigth {
    .mainweb {
      color: #ff6600;
    }
  }
}
</style>