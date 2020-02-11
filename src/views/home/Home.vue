<template >
  <div class="wrapper" id="home">
    <nav-bar class="home-nav">
      <template v-slot:center>
        <div>
          <p>购物街</p>
        </div>
      </template>
    </nav-bar>
    <home-swiper :banners="banners"></home-swiper>
  </div>
</template>

<script>
import NavBar from "components/common/navbar/NavBar.vue";
import HomeSwiper from "./childComps/HomeSwiper";
import { getHomeMultidata } from "network/home";

export default {
  components: {
    NavBar,
    HomeSwiper
  },
  props: {},
  data() {
    return {
      result: null,
      banners: [],
      recommends: []
    };
  },
  watch: {},
  computed: {},
  methods: {},
  created() {
    getHomeMultidata().then(res => {
      console.log(res);
      this.result = res;
      this.banners = res.data.banner.list;
      this.recommends = res.data.recommend.list;
    });
  },
  mounted() {}
};
</script>
<style  scoped>
.home-nav {
  background-color: var(--color-tint);
  color: #fff;
}
</style>