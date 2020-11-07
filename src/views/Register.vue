<!--
/**
 * @name 'Register'
 * @desc '注册页面'
 * @author 'duqy'
 * @time 2020年11月04日 22:20:15 Wednesday
 */
-->
<template>
  <div id="div_content">
    <img alt="Vue logo" src="../assets/logo.png" />
    <van-form @submit="onSubmit">
      <van-field
        v-model="username"
        name="客户姓名"
        label="客户姓名"
        placeholder="客户姓名"
        :rules="[{ required: true, message: '请填写客户姓名' }]"
      />
      <van-field
        v-model="phone"
        name="手机号码"
        label="手机号码"
        placeholder="手机号码"
        :rules="[{ required: true, message: '请填写手机号码' }]"
      />
      <van-field
        v-model="plat"
        name="报备平台"
        label="报备平台"
        placeholder="报备平台"
        :rules="[{ required: true, message: '请填写报备平台' }]"
      />

      <van-field
        v-model="date"
        name="选择日期"
        label="选择日期"
        placeholder="选择日期"
        :rules="[{ required: true, message: '请填写报备平台' }]"
        @focus="show = true"
      />
      <van-calendar v-model="show" color="#3e8df8" @confirm="onConfirm" />
      <div style="margin: 20px 10px 10px 10px; padding:20px 0px 0px 0px ">
        <van-button round block type="info" native-type="submit">
          提 交
        </van-button>
      </div>
    </van-form>
  </div>
</template>

<script>
export default {
  name: "Register",
  components: {},
  data() {
    return {
      active: 2,
      date: "2020-11-05",
      username: '老张',
      phone: '15874988763',
      plat: '钱站',
      show: false,
    };
  },
  props: {
    msg: String,
  },
  computed: {
    
  },
  methods: {
    onConfirm(date) {
      this.show = false;
      this.date = this.formatDate(date);
    },
    formatDate(date) {
      console.log(date);
      console.log(date.getFullYear());
      return `${date.getFullYear()}-${date.getMonth() + 1}-${date.getDate()}`;
    },
    onSubmit() {
      this.$router.push({ path: "/result", query: {
        username: this.username,
        plat: this.plat,
        date: this.date,
        phone: this.phone
      } });
    },
  },
  watch: {},
  created() {},
  mounted() {},
  destroyed() {},
};
</script>
<style lang='less' scoped>
.div_content {
  padding: 10px;
}
</style>
