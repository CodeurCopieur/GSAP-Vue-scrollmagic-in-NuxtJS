<template>
  <div>
    <div id="title">Hello World</div>
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
  #title {
    width: 350px;
    height: 350px;
  }
</style>
