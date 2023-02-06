<template>
  <div class="body">
    <div class="wrapper">
      <div class="display">
        <div id="time">{{ hours }}:{{ minutes }}:{{ seconds }} {{ ampm }}</div>
      </div>
      <span></span>
      <span></span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      hours: "00",
      minutes: "00",
      seconds: "00",
      ampm: "AM",
    };
  },
  mounted() {
    setInterval(() => {
      const date = new Date();
      let hours = date.getHours();
      this.ampm = hours >= 12 ? "PM" : "AM";
      this.hours = (hours % 12 || 12).toString().padStart(2, "0");
      this.minutes = date.getMinutes().toString().padStart(2, "0");
      this.seconds = date.getSeconds().toString().padStart(2, "0");
    }, 1000);
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  font-family: "poppins", sans-serif;
}

.body {
  display: grid;
  height: 100vh;
  place-items: center;
  background: #000;
}

.wrapper {
  height: 100px;
  width: 360px;
  cursor: default;
  background: linear-gradient(135deg, #14ffe9, #ffeb3b, #ff00e0);
  border-radius: 10px;
  animation: animate 1.5s linear infinite;
}

.wrapper .display,
.wrapper span {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.wrapper .display {
  background: #1b1b1b;
  height: 85px;
  width: 345px;
  border-radius: 6px;
  text-align: center;
}

.wrapper .display #time {
  line-height: 85px;
  color: #fff;
  font-size: 50px;
  font-weight: 600;
  letter-spacing: 1px;
  background: linear-gradient(135deg, #14ffe9, #ffeb3b);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

@keyframes animate {
  100% {
    filter: hue-rotate(360deg);
  }
}
</style>
