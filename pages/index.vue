<template>
  <div>
    <div class="blank">
      <div class="circle circle-small"></div>
      <div class="circle circle-large"></div>
    </div>
    <div class="wrapper">
      <div class="img-1"/>
      <h2 class="title1">Lorem ipsum dolor <br> sit amet consectetur</h2>

      <div class="img-2"/>
      <h2 class="title2">Lorem ipsum dolor <br> sit amet consectetur</h2>
    </div>
    <div class="overlay">
      <div class="layer layer-1"></div>
      <div class="layer layer-2"></div>
      <div class="layer layer-3"></div>
    </div>
  </div>
</template>

<script>
import { gsap } from "gsap";

export default {
  mounted : function(){
    this.start()
    this.startAnimations()
  },
  methods: {
    start() {
      gsap.fromTo(
        ".circle-small",
        { y: "20rem", opacity: 0 },
        { y: 0, opacity: 1, ease: "back.out(1.7)", delay: 1 }
      );

      gsap.fromTo(
        ".circle-large",
        { x: "20rem", opacity: 0 },
        { x: 0, opacity: 1, ease: "back.out(1.7)", delay: 1.5 }
      );

      gsap.to(".layer-1", { y: "-100vh", delay: 0.5 });
      gsap.to(".layer-2", { y: "-100vh", delay: 0.7 });
      gsap.to(".layer-3", { y: "-100vh", delay: 0.93 });
    },
    startAnimations: function() {
      var tl = new TimelineMax({onUpdate:updatePercentage})
      // la timeline va être controler par le pourcentage de scroll definit par scrollMagic

      // Declare Scene
      const scene = this.$scrollmagic.scene({
        // ID of element where animation starts
        triggerElement: '.wrapper',
        // {0,0.5,1} - animations starts from {top,center,end} of window
        triggerHook: 0,
        // Duration of animation
        duration: "300%"

      })
      .setPin(".wrapper")
      .setTween(tl)

      this.$scrollmagic.scene(scene)

      function updatePercentage() {
        tl.progress()
      }
    }
  }
}
</script>

<style lang="scss">
  @import url('../assets/scss/index.scss');
  div {
    font-family:sans-serif;

    .blank {
      width: 100%;
      height: 100vh;
      background-color: #293546;
      overflow: hidden;
      position: relative;
      .circle  {
        position: absolute;
      }
      .circle-small {
        width: 25rem;
        height: 25rem;
        border-radius: 50%;
        top: -7rem;
        left: -5rem;
        background-color: #021226;
        transition: all 480ms;

        &:before {
          content: "";
          position: absolute;
          width: 12rem;
          height: 12rem;
          border-radius: inherit;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          background-color: #293546;
          transition: all 480ms;
        }
      }
      .circle-large {
        width: 100rem;
        height: 100rem;
        border-radius: 50%;
        bottom: -40rem;
        right: -50rem;
        background-color: #fff;
        -webkit-transition: all 480ms;
        -o-transition: all 480ms;
        transition: all 480ms;
        
        &::before{
          content: "";
          position: absolute;
          width: 55rem;
          height: 55rem;
          border-radius: inherit;
          top: 50%;
          left: 50%;
          transform: translate(-50%, -50%);
          background-color: #293546;
          transition: all 480ms;
        }
      }
    }
    .wrapper  {
      width: 100%;
      height: 100vh;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: flex-end;
      overflow: hidden;
      background-color: #293546;
      border-top: 1px solid #fff;
      border-bottom: 1px solid #fff;

      .title1 {
        position: absolute;
        top: 50%;
        left: 20%;
        transform: translate(-50%, -50%);
        font-size: 35px;
        color: red;
        opacity: 0;
      }

      .img-1 {
        background-image: url('https://i.picsum.photos/id/1032/2880/1800.jpg?hmac=5SLBdyPZBMyr5IBkIRfffZV10bP87Y7RrxVZX1vCefA');
        width: 60%;
        height: 60%;
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center center;
      }

      .img-2 {
        background-image: url('https://i.picsum.photos/id/1002/4312/2868.jpg?hmac=5LlLE-NY9oMnmIQp7ms6IfdvSUQOzP_O3DPMWmyNxwo');
        position: absolute;
        width: 100%;
        height: 0;
        bottom: 0;
        left: 50%;
        transform: translate(-50%, 0);
        background-size: cover;
        background-repeat: no-repeat;
        background-position: center bottom;
      }

      .title2 {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        font-size: 60px;
        color: red;
        line-height: 60px;
    }
  }
    
    .overlay {
      width: 100%;
      height: 100vh;
      position: relative;
      overflow: hidden;
      z-index: 999;
      display: flex;
      top: 0;
      left: 0;
      background-color: #293546;

      .layer {
        background-color: #07172b;
      }

      .layer-1, .layer-2, .layer-3 {
          flex: 1;
      }
    }
  }
</style>
