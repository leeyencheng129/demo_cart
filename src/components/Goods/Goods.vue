<template>
  <div class="goods">
    <!-- 左側 -->
    <div class="thumb">
      <div class="custom_control custom_checkbox">
        <input
          type="checkbox"
          class="custom_control_input"
          id="cb1"
          :checked="status"
          @change="stateChange"
        />
        <label class="custom_control_label" for="cb1">
          <img :src="pic" alt="" />
        </label>
      </div>
    </div>
    <!-- 右側 -->
    <div class="goods_info">
      <h6 class="goods_title">{{ title }}</h6>
      <div class="goods_info_bottom">
        <span class="goods_price">${{ price }}</span>
        <!-- 商品數量 -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    id: {
      require: true,
      type: Number,
    },
    title: {
      default: "",
      type: String,
    },
    pic: {
      default: "",
      type: String,
    },
    price: {
      default: "",
      type: Number,
    },
    status: {
      default: true,
      type: Boolean,
    },
  },
  methods: {
    stateChange(e) {
      const newState = e.target.checked;
      this.$emit("state-change", { id: this.id, value: newState });
    },
  },
};
</script>
<style lang="less" scoped>
.goods {
  display: flex;
  border: 1px solid #eee;
  padding: 2% 0;
}
.thumb {
  width: 30%;
  .custom_control {
    display: flex;
    align-items: center;
    justify-content: space-evenly;
  }
}
.goods_info {
  width: 70%;
  display: flex;
  flex-wrap: wrap;
  align-content: space-around;
  padding-right: 5%;
  .goods_title {
    font-size: 30px;
  }
  .goods_info_bottom {
    display: block;
    width: 100%;
    .goods_price {
      color: rgb(189, 7, 7);
      font-weight: 700;
      font-size: 26px;
    }
  }
}
</style>
