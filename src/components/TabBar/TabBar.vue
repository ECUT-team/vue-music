<template>
  <div class="tabbar">
    <router-view />
    <ul class="tabItem">
      <li v-for="item in tabData" :key="item.name"  class="tabTo" @click="tabClick(item.path)">
        <img class="tabImg" :src="item.path== $route.path?item.activeImg:item.img" />
        <div :class="{'active':item.path== $route.path}" class="tabText">{{item.name}}</div>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      tabData: [
        {
          path: "/",
          img: require("@/assets/images/home.png"),
          activeImg: require("@/assets/images/home2.png"),
          name: "音乐"
        },
        {
          path: "/me",
          img: require("@/assets/images/me.png"),
          activeImg: require("@/assets/images/me2.png"),
          name: "我"
        }
      ]
    };
  },
  methods: {
    tabClick(path) {
      this.$router.push(path);
      this.$emit("change", path);
    }
  }
};
</script>
<style lang="less" scoped>
 

</style>