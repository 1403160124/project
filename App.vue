<template>
  <div>
    <Header />
    <!-- 路由组件出口的地方 -->
    <router-view></router-view>
    <!-- 在Home与Search可见的，但是Login|Register不可见 -->
    <!-- 利用路由元信息解决当前问题好处：一行代码就可以解决 -->
    <Footer v-show="$route.meta.isShow" />
  </div>
</template>

<script>
//引入Header与Footer非路由组件
import Header from "./components/Header";
import Footer from "./components/Footer";
export default {
  name: "",
  data() {
    return {
      msg: "abc"
    }
  },
  components: {
    Header,
    Footer,
  },
  mounted() {
    //派发一个action||获取商品分类的三级列表的数据,通知仓库发送请求把服务器的数据放在仓库里，避免了每次使用typeNav都向服务器发请求
    //this 指向vc，vc中才有$store
    this.$store.dispatch("getCategoryList");
  },
};
</script>

<style scoped></style>
