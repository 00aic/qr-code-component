<template>
  <div class="qr-code">
    <div class="qr-code__container">
      <vue-qrcode :value="text" :options="options" tag="svg" class="qr-code__container-svg" />
    </div>
    <div class="qr-code__desc">
      <div class="qr-code__desc-title">Improve your front-end skills by building projects</div>
      <div class="qr-code__desc-step">
        Scan the QR code to visit Frontend Mentor and take your coding skills to the next level
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import VueQrcode from '@chenfengyuan/vue-qrcode'

const props = defineProps({
  text: {
    type: String,
    default: 'Improve your front-end skills by building projects',
  },
  size: {
    type: Number,
    default: 170,
  },
  bgColor: {
    type: String,
    default: '#3685ff', // 蓝色背景
  },
  qrColor: {
    type: String,
    default: '#ffffff', // 二维码白色
  },
})

const options = computed(() => ({
  width: props.size,
  margin: 1,
  color: {
    dark: props.qrColor, // 二维码
    light: props.bgColor, // 背景色
  },
}))
</script>

<style lang="scss" scoped>
.qr-code {
  background-color: white;
  box-sizing: border-box;
  box-shadow: 0px 25px 25px rgba(0, 0, 0, 0.0477);

  border-radius: 20px;
  padding: 16px 16px 40px;
  width: 320px;
  height: 499px;
  display: flex;
  flex-direction: column;
  gap: 24px;

  &__container {
    background-color: v-bind('props.bgColor');
    width: 288px;
    height: 288px;
    display: flex;
    justify-content: center;
    align-content: center;
    border-radius: 10px;
    flex-wrap: wrap;
  }
  &__desc {
    display: flex;
    flex-direction: column;
    text-align: center;
    gap: 16px;
    padding: 0 16px;

    &-title {
      font-weight: bold;
      font-size: 20px;
      line-height: 1.2;
      letter-spacing: 0;
    }
    &-step {
      color: hsl(216, 15%, 48%);
      font-size: 14px;
      line-height: 1.4;
      letter-spacing: 0.2px;
    }
  }
}
</style>
