<template>
  <div class="parent">
    <div class="container">
      <div class="card1" ref="card1">
        <div class="number">{{ 10 > number ? "0" + number : number }}</div>
      </div>
      <div class="card2">
        <div class="number">{{ 10 > number ? "0" + number : number }}</div>
      </div>
    </div>
    <p>{{ title }}</p>
  </div>
</template>
<script>
  export default {
    props: ["title", "number"],
    data() {
      return {
        flip: false,
      };
    },

    created() {},
  };
</script>

<style lang="scss" scoped>
  .parent {
    display: flex;
    flex-direction: column;
    text-align: center;
    margin-left: 50px;
    p {
      color: hsl(237, 18%, 59%);
      font-size: 1.1rem;
      letter-spacing: 8px;
      margin-top: 15px;
      text-transform: uppercase;
    }
  }
  .container {
    overflow: hidden;
    height: 170px;
    width: 170px;
    background-color: hsl(236, 21%, 26%);
    border-radius: 10px;
    perspective: 400px;

    .card1,
    .card2 {
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 7rem;
      height: 47%;
      color: hsl(345, 95%, 68%);
      background-color: hsl(236, 21%, 26%);
    }
    // .flipCard {
    //   animation: cardFlip 1s ease-out;
    // }

    .card1 {
      overflow: hidden;

      z-index: 2;
      filter: brightness(0.93);

      border-bottom: 1px solid hsl(234, 17%, 12%);
      border-radius: 8px 8px 0 0;
      transform-origin: bottom;
      transform-style: preserve-3d;

      .number {
        position: absolute;
        bottom: -15px;
        height: 100%;
      }
      &::before {
        content: "";
        position: absolute;
        height: 17px;
        width: 17px;
        z-index: 2;

        bottom: -10px;
        border-radius: 50%;
        left: -10px;
        background-color: hsl(234, 17%, 12%);
      }
      &::after {
        content: "";
        position: absolute;
        height: 17px;
        width: 17px;
        bottom: -10px;
        z-index: 2;

        border-radius: 50%;
        right: -10px;
        background-color: hsl(234, 17%, 12%);
      }
    }
    .card2 {
      z-index: 1;
      background-color: #3a3c58;
      box-shadow: 0px 12px 1px hsl(234, 17%, 12%);

      border-radius: 0 0 8px 8px;

      .number {
        position: absolute;
        top: -66px;
        height: 100%;
      }
      &::before {
        content: "";
        position: absolute;
        height: 17px;
        width: 17px;
        top: -10px;
        border-radius: 50%;
        z-index: 2;

        left: -10px;
        background-color: hsl(234, 17%, 12%);
      }
      &::after {
        content: "";
        position: absolute;
        height: 17px;
        z-index: 2;
        width: 17px;
        top: -10px;
        border-radius: 50%;
        right: -10px;
        background-color: hsl(234, 17%, 12%);
      }
    }
  }
  // @keyframes cardFlip {
  //   0% {
  //     transform: rotateX(0deg);
  //   }

  //   90% {
  //     opacity: 1;
  //   }
  //   100% {
  //     transform: rotateX(-93deg);
  //     opacity: 0;
  //   }
  // }
</style>
