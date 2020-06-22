<template>
  <div>
    <div class="blank"></div>
      <div class="wrapper">
        <div class="img-1"/>
        <h2 class="title1">Lorem ipsum dolor <br> sit amet consectetur.</h2>

        <div class="img-2"/>
        <h2 class="title2">Lorem ipsum dolor <br> sit amet consectetur.</h2>
      </div>
    <div class="blank"></div>
  </div>
</template>

<script>

  import { gsap } from "gsap";

export default {
  mounted : function(){
    this.start()
  },
  methods: {
    start() {
      gsap.to('#title', {duration: 1, color: "red"})
    }
  }
}
</script>

<style>
@import url('../assets/scss/index.scss');

</style>
