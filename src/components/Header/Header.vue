<template>
  <div class="container">
    <h1>{{ title }}</h1>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      default: "",
      type: String,
    },
  },
};
</script>

<style lang="less" scoped>
h1 {
  color: #fff;
  background: rgb(17, 214, 165);
  text-align: center;
  line-height: 2;
}
</style>
