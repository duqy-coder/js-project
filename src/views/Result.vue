<!--
/**
 * @name 'Result'
 * @desc '报备结果页面'
 * @author 'duqy'
 * @time 2020年11月04日 23:48:26 Wednesday
 */
-->
<template>
  <div id="div_body">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <van-nav-bar
      title="报备结果"
      left-text="返回"
      left-arrow
      :fixed=true
      @click-left="onClickLeft"
      @click-right="onClickRight"
    >
    </van-nav-bar>

    <div id="div_content">
      <van-steps :active="active" active-color="#38f">
        <van-step>资料认证</van-step>
        <van-step>预审批</van-step>
        <van-step>报 备</van-step>
        <van-step>放款</van-step>
      </van-steps>
      <div class="div_line_space"></div>
      <div id="div_note_1">
        <van-icon name="passed" />内部员工验证已通过，登陆成功！
      </div>
      <h4>报备客户资料：</h4>
      <div class="div_span">客户姓名：{{ username }}</div>
      <div class="div_span">手机号码：{{ jmPhone }}</div>
      <div class="div_span">报备平台：{{ plat }}</div>
      <div class="div_span">报备状态：报备成功</div>
      <div class="div_span">报备时间：{{ date }}</div>
      <p style="margin: 40px">&nbsp;</p>
      <div id="div_note">
        已报备通过 可以用于特定商户消费 未开放提现权限 请勿提现
      </div>
       
    </div>
    <div class="div_line_space"></div>
    <div class="div_line_space"></div>
    <div style="margin: 20px 10px 10px 10px; padding: 20px 0px 0px 0px">
      <van-button type="info" block round @click="onClickLeft"
        >返回上一级</van-button
      >
    </div>
  </div>
</template>

<script>
export default {
  name: "Result",
  components: {},
  data() {
    return {
      active: 2,
      icon: {
        active: "https://img.yzcdn.cn/vant/user-active.png",
        inactive: "https://img.yzcdn.cn/vant/user-inactive.png",
      },
      date: "",
      username: null,
      phone: null,
      plat: null,
      show: false,
      jmPhone: null
    };
  },
  props: {},
  computed: {
     
  },
  methods: {
    onClickLeft() {
      console.log("返回");
      // this.$router.push('/')
      this.$router.go(-1);
    },
    onClickRight() {
      console.log("按钮");
      this.$router.go(-1);
    },
  },
  watch: {
    phone: function(val){
      if(val){
        this.jmPhone =  val.substring(0, 3) + '*****' + val.substring(8, val.length);
      }
    }
  },
  created() {},
  mounted() {
    this.$nextTick(() => {
      this.username = this.$route.query.username;
      this.plat = this.$route.query.plat;
      this.date = this.$route.query.date;
      this.phone = this.$route.query.phone;
    });
  },
  destroyed() {},
};
</script>
<style scoped lang="less">
#div_note_1 {
  color: black;
  margin-bottom: 20px;
}
#div_note {
  color: red;
  margin-bottom: 20px;
}
.div_span {
  padding-bottom: 5px;
}
#div_content {
  padding-left: 16px;
  padding-right: 16px;
  text-align: left;
}
.van-icon {
  color: blue;
  margin-right: 10px;
}
.div_line_space {
  padding: 15px;
}
#div_body {
  font-size: 14px;
}
</style>
