<template>
  <header>
    <div>We're Launching Soon</div>
  </header>
  <div class="parent-container">
    <the-card title="days" :number="days"></the-card>
    <the-card title="hours" :number="hours"></the-card>

    <the-card title="minutes" :number="minutes"></the-card>
    <the-card title="seconds" :number="seconds"></the-card>
  </div>
  <footer>
    <div class="contact">
      <img src="./images/icon-facebook.svg" alt="" />
      <img src="./images/icon-pinterest.svg" alt="" />
      <img src="./images/icon-instagram.svg" alt="" />
    </div>
    <img src="./images/pattern-hills.svg" alt="pattern-hills" />
  </footer>
</template>

<script>
  import TheCard from "./components/TheCard.vue";
  export default {
    data() {
      return {
        days: 14,
        hours: 23,
        minutes: 59,
        seconds: 59,
        timer: null,
        end: false,
      };
    },
    components: {
      TheCard,
    },
    watch: {
      days(value) {
        if (value < 0) {
          this.endTimer();
        }
      },
      hours(value) {
        if (value === 0 && !this.end) {
          this.hours = 23;
          this.getDays();
        }
      },
      minutes(value) {
        if (value === 0 && !this.end) {
          this.minutes = 59;
          this.getHours();
        }
      },
      seconds(value) {
        if (value === 0 && !this.end) {
          this.getMinutes();
          this.seconds = 59;
        }
      },
    },
    methods: {
      getMinutes() {
        --this.minutes;
      },
      getHours() {
        --this.hours;
      },
      getDays() {
        --this.days;
      },
      endTimer() {
        this.end = true;
        clearInterval(this.timer);
        this.days = 0;
        this.hours = 0;
        this.minutes = 0;
        this.seconds = 0;
      },
    },
    created() {
      this.timer = setInterval(() => {
        --this.seconds;
      }, 1000);
    },
  };
</script>
<style lang="scss">
  @import url("https://fonts.googleapis.com/css2?family=Red+Hat+Text:wght@700&display=swap");
  * {
    box-sizing: border-box;
  }
  html,
  body {
    margin: 0;
    padding: 0;
    font-size: 14px;
    height: 100%;
    font-family: "Red Hat Text";
    background-color: hsl(235, 16%, 14%);
    background-image: url("./images/bg-stars.svg");
    background-size: cover;
  }
  #app {
    height: 100%;
  }
  header {
    height: 30%;
    display: flex;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 1.4rem;
    letter-spacing: 8px;
    text-transform: uppercase;
  }
  .parent-container {
    height: calc(50% - 140px);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  footer {
    width: 100%;
    position: absolute;
    bottom: 0;
    display: flex;
    justify-content: center;
    .contact {
      position: absolute;
      width: 15%;
      top: 50%;
      display: flex;
      justify-content: space-around;
      img {
        cursor: pointer;
        width: 25px;
        height: auto;
        &:hover {
          filter: contrast(20);
        }
      }
    }
    img {
      width: 100%;
    }
  }
</style>
