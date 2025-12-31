<script setup>
const props = defineProps({
  class: String,
  title: String,
});
console.log(props, "=====");
</script>
<template>
  <div :class="`card ${props.class}`">
    <div class="card-top">
      <div class="card-top-left"></div>
      <div class="card-top-right">
        <div class="dot"></div>
        <div class="title">{{ props.title }}</div>
      </div>
    </div>
    <div class="card-content">
      <slot></slot>
    </div>
  </div>
</template>
<style scoped>
.card {
  height: 100%;
  background: #122953;
  border-radius: 0px 0px 0px 0px;
  box-sizing: border-box;
  border: 2px solid;
  border-image: linear-gradient(
      180deg,
      rgba(
        54.00000058114529,
        133.00000727176666,
        244.0000006556511,
        0.6313725709915161
      ),
      rgba(44.000001177191734, 84.00000259280205, 137.00000703334808, 1)
    )
    2 2;
  display: flex;
  flex-direction: column;
}
.card-top {
  height: 44px;
  display: flex;
  flex: none;
}
.card-top-left {
  width: 8.5px;
  height: 100%;
  margin-right: 5px;
  background-image: url("../../public/card-top-left.png");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
}
.card-top-right {
  flex: 1;
  height: 100%;
  background-image: url("../../public/card-top-right.png");
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  box-sizing: border-box;
  padding-left: 18px;
  display: flex;
  align-items: center;
}
.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background-color: #28effa;
  margin-right: 10.5px;
}
.title {
  font-size: 18px;
  color: #fff;
  font-weight: 500;
  text-shadow: 0px 1px 12px rgba(27, 126, 242, 0.91);
}
.card-content {
  width: 100%;
  flex: 1;
}
.w-100 {
  flex: 1;
}
.w-60 {
  flex: 6;
}
.w-40 {
  flex: 4;
}
.w-50 {
  flex: 5;
}
.w-36 {
  flex: 3.6;
}
.mr-8 {
  margin-right: 8px;
}
</style>
