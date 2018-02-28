<template>
  <div class="welcome__bubbles">
    <div class="bubble bubble_lg"></div>
    <div class="bubble bubble_lg"></div>
    <div class="bubble bubble_md"></div>
    <div class="bubble bubble_md"></div>
    <div class="bubble bubble_md"></div>
    <div class="bubble bubble_sm"></div>
    <div class="bubble bubble_sm"></div>
    <div class="bubble bubble_sm"></div>
  </div>
</template>

<script>
export default {
  name: 'Bubbles',
  // data () {
  //   return {
  //     bubleStatus: true
  //   }
  // },
  mounted () {
    this.styleBubbles()
  },
  methods: {
    styleBubbles: function () {
      let bubbles = document.getElementsByClassName('bubble')
      let animationWidth = window.innerWidth
      let animationHeight = window.innerHeight

      let maxPositionWidth = animationWidth * 0.001
      let maxPositionHeight = animationHeight * 0.001

      for (let i = 0; i < bubbles.length; i++) {
        let duration = (Math.random() * (0.2 - 0.07) + 0.07).toFixed(3)
        let topPosition = (Math.random() * (maxPositionHeight - 0.001) + 0.001).toFixed(4)
        let leftPosition = (Math.random() * (maxPositionWidth - 0.001) + 0.001).toFixed(4)

        bubbles[i].style.top = topPosition * 100 + 'rem'
        bubbles[i].style.left = leftPosition * 100 + 'rem'
        bubbles[i].style.animationDuration = duration * 1000 + 's'
        bubbles[i].style.animationDelay = duration * 10 + 's'
        bubbles[i].style.filter = 'blur(' + (Math.random() * (0.4 - 0) + 0).toFixed(1) + 'rem)'
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
  @import '../../scss/variables';

  // Bubbles
  .bubble {
    border-radius: 100%;
    color: $white;
    background-color: currentColor;
    position: absolute;
    // animation-name: moveBubble;
    animation-iteration-count: infinite;
    animation-timing-function: ease-in-out;
    transition: all 3s linear;

    .welcome__intro_active & {
      color: $concrete;
    }

    &:before, &:after {
      content: '';
      display: block;
      background-color: currentColor;
      border-radius: 100%;
      transition: all 3s linear;
    }
    &:before {
      transform: translate(800%, 100%);
      filter: blur(.1rem);
      width: 90%;
      height: 90%;
    }
    &:after {
      transform: translate(-100%, -800%);
      width: 120%;
      height: 120%;
      filter: blur(0);
    }

    &_lg {
      width: 16.8rem;
      height: 16.8rem;
    }
    &_md {
      width: 9.8rem;
      height: 9.8rem;
    }
    &_sm {
      width: 3.8rem;
      height: 3.8rem;
    }
  }

  @keyframes moveBubble {
    0% {
      transform: translate(0, 0);
    }
    50% {
      transform: translate(-600%, -1000%);
    }
    100% {
      transform: translate(0, 0);
    }
  }
</style>
