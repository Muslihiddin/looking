<template>
  <div class="morty" @mousemove="mouseMove">
    <div class="center" ref="anchor"></div>
    <img
      class="eye"
      src="../src/assets/eye.png"
      alt="eye"
      style="top: 34%; right: 42.5%"
      :style="{ transform: `rotate(${90 + angleDeg}deg)` }"
    />
    <img
      class="eye"
      src="../src/assets/eye.png"
      alt="eye"
      style="top: 33.5%; right: 36.5%"
      :style="{ transform: `rotate(${90 + angleDeg}deg)` }"
    />
    <img
      class="eye"
      src="../src/assets/eye.png"
      alt="eye"
      style="bottom: 31.5%; left: 46.5%"
      :style="{ transform: `rotate(${90 + angleDeg}deg)` }"
    />
    <img
      class="eye"
      src="../src/assets/eye.png"
      alt="eye"
      style="bottom: 28.5%; left: 39.7%"
      :style="{ transform: `rotate(${90 + angleDeg}deg)` }"
    />
    <img src="../src/assets/talk.png" alt="" />
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      rekt: null,
      anchorX: null,
      anchorY: null,
      angleDeg: null,
    };
  },
  mounted() {
    this.rekt = this.$refs.anchor.getBoundingClientRect();
    this.anchorX = this.rekt.left + this.rekt.width / 2;
    this.anchorY = this.rekt.top + this.rekt.height / 2;
  },
  methods: {
    mouseMove(event) {
      const mouseX = event.clientX;
      const mouseY = event.clientY;

      this.angleDeg = this.angle(mouseX, mouseY, this.anchorX, this.anchorY);
    },
    angle(cx, cy, ex, ey) {
      const dy = ey - cy;
      const dx = ex - cx;
      const rad = Math.atan2(dy, dx);
      const deg = (rad * 180) / Math.PI;
      return deg;
    },
  },
};
</script>
<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  color: white;
  background-color: black;
}
.morty {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100vw;
  height: 100vh;
  background-image: url("../src/assets/morty.png");
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}

.eye {
  position: absolute;
  border-radius: 50%;
}

.center {
  width: 550px;
  height: 550px;
}
</style>
