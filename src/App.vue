<template>
  <div id="app">
    <Header title="購物車實例"></Header>

    <!-- 循環每個商品的資訊 -->
    <Goods
      v-for="item in list"
      :key="item.id"
      :id="item.id"
      :title="item.goods_name"
      :pic="item.goods_img"
      :price="item.goods_price"
      :status="item.goods_state"
      @state-change="getNewState"
    ></Goods>
  </div>
</template>

<script>
import Reset from "@/assets/css/style.css";
//導入axios
import axios from "axios";
//導入組件
import Header from "@/components/Header/Header.vue";
import Goods from "@/components/Goods/Goods.vue";

export default {
  data() {
    return {
      list: [],
    };
  },
  created() {
    this.initCartList();
  },
  methods: {
    async initCartList() {
      const { data: res } = await axios.get("https://www.escook.cn/api/cart");
      console.log(res);
      if (res.status === 200) {
        this.list = res.list;
      }
    },
    getNewState(val) {
      console.log(val);
    },
  },
  components: {
    Header,
    Goods,
  },
};
</script>

<style lang="less" scoped>
#app {
  margin: 0;
  padding: 0;
}
</style>
