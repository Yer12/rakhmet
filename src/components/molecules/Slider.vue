<template>
  <section class="slider">
    <div class="slider-container">
      <div class="slider-item" v-for="(imgs,i) in restaurant_images" :key="i">

        <img :src="imgs.url" alt="">
      </div>
      <div class="slider_info">
        1/{{restaurant_images.length}}
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: "Slider",
  props: {
    restaurant_images: {
      type: Array
    }
  }
}
</script>

<style scoped>
/*Slider*/
.slider {
  width: 100%;
  height: 172px;
  position: relative;
}
.slider-container {
  width: 100%;
  overflow-x: scroll;
  white-space: nowrap;
}
.slider-container::-webkit-scrollbar {
  display: none;
}
.slider-item {
  display: inline-block;
  position:relative;
  background: #8F8F8F;
  width: 100vw;
  height: 172px;
}
.slider-item img {
  width: 100%;
  height: 172px;
}
.slider_info {
  background: #FFFFFF;
  opacity: 0.8;
  border-radius: 4px;
  position: absolute;
  bottom: 16px;
  left: 16px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: normal;
  font-size: 12px;
  line-height: 18px;
  width: 47px;
  height: 21px;
}
</style>
