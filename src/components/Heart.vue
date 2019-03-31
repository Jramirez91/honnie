<template>
  <div class="body-doc">
    <div class="back"></div>
    <div
      id="button"
      class="tool-tip"
      v-on:click="moveAbout"
      data-tooltip-title="Top tooltip"
      data-tooltip-position="top"
    >
      <!--<img src="https://pp.vk.me/c624230/v624230976/43e7b/T5WjDtwt80M.jpg" alt="" />-->
      <svg
        version="1.1"
        id="Capa_1"
        xmlns="http://www.w3.org/2000/svg"
        xmlns:xlink="http://www.w3.org/1999/xlink"
        x="0px"
        y="0px"
        class="b-heart"
        width="45.412px"
        height="45.413px"
        viewBox="0 0 45.412 45.413"
        style="enable-background:new 0 0 45.412 45.413;"
        xml:space="preserve"
      >
        <g>
          <path
            class="hrt"
            d="M45.412,16.024c0-6.918-5.668-12.547-12.635-12.547c-4.103,0-7.754,1.951-10.063,4.969
			c-2.311-3.018-5.965-4.969-10.07-4.969C5.672,3.477,0,9.105,0,16.024c0,10.422,14.892,25.911,22.715,25.911
			c1.185,0,2.531-0.358,3.965-0.998c0,0-5.476-4.086-7.683-5.672C13.625,31.402,5.143,22.639,5.143,16.024
			c0-4.082,3.365-7.403,7.5-7.403c4.135,0,7.5,3.321,7.5,7.403c0,1.42,1.151,2.572,2.572,2.572c1.42,0,2.57-1.152,2.57-2.572
			c0-4.082,3.361-7.403,7.492-7.403s7.492,3.321,7.492,7.403c0,6.723-8.544,15.977-14.113,19.411l4.394,3.244
			C37.761,33.575,45.412,23.497,45.412,16.024z"
          ></path>
        </g>
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "Heart",
  methods: {
    addHeart: function() {
      var color = ["#f9a363", "#8c1346", "#d13d3c", "#e2663b"];
      var randomColor = Math.floor(Math.random() * 4);
      var randomX = Math.floor(Math.random() * 100);
      var randomY = Math.floor(Math.random() * 100);
      var stringContainingSVGSource = `<svg style="top:${randomY}%; left:${randomX}%;" class="heart" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 23.217 23.217"  xml:space="preserve"><g><path style="fill:${
        color[randomColor]
      };" d="M11.608,21.997c-22.647-12.354-6.268-27.713,0-17.369C17.877-5.716,34.257,9.643,11.608,21.997z" /></g></svg>`;

      var parser = new DOMParser();
      var doc = parser.parseFromString(
        stringContainingSVGSource,
        "image/svg+xml"
      );
      var app = document.getElementById("app");
      document.body.insertBefore(doc.documentElement, app);
    },
    deleteHearts: function() {
      var dch = document.querySelectorAll(".heart");
      for (let index = 30; index < dch.length; index++) {
        const element = dch[index];
        element.remove();
      }
    },
    centerHeart: function() {
      var chs = document.querySelectorAll(".heart");
      for (let index = 0; index < chs.length; index++) {
        const element = chs[index];
        element.classList.add("start-animate");
      }
    },
    moveAbout: function() {
      this.$router.push({ path: "about" });
    }
  },
  mounted() {
    setInterval(this.addHeart, 200);
    setInterval(this.centerHeart, 200);
    setInterval(this.deleteHearts, 500);
  }
};
</script>

<style lang="scss">
body {
}
.back {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background: url(http://artem.anmedio.ru/dev/denis/1+2jpg) center center
    #22181e no-repeat;
  background-size: cover;
}

#source-heart {
  width: 20px;
  height: 20px;
  position: fixed;
  right: 30px;
  top: 30px;
}
.hrt {
  fill: #ffdcb9;
}
.hrt:hover {
  fill: rgb(173, 23, 23);
}

#button {
  width: 100px;
  height: 100px;
  left: 50%;
  top: 50%;
  margin: -50px;
  background: #22181e;
  position: fixed;
  border-radius: 50px;
  box-sizing: border-box;
  color: black;
  text-align: center;
  padding: 25px 0 0 3px;
  font-family: monospace;
  font-size: 40px;
  cursor: pointer;
  z-index: 20;
  box-shadow: 0 0 20px -5px #22181e;
  overflow: hidden;
  img {
    position: absolute;
    left: -73%;
    top: 0;
    width: 180%;
  }
  svg {
    width: 50%;
    height: 50%;
    left: 50%;
    top: 50%;
    position: absolute;
    transform: translateX(-50%) translateY(-45%);
  }
}
.heart {
  position: fixed;
  width: 50px;
  z-index: 50;
  height: 50px;
  transform: translateX(-50%) translateY(-50%) scale(1.5);
  opacity: 1;
  transition: 0.5s ease;
  opacity: 0;
}
.start-animate {
  animation: show-heart 10s ease infinite;
}

@keyframes show-heart {
  0% {
    opacity: 0;
    transform: translateX(-50%) translateY(-50%) scale(1.5) rotateZ(-15deg);
  }
  50% {
    opacity: 0.8;
    //transform:translateX(-50%) translateY(-50%) scale(1) rotateZ(30deg);
  }
  100% {
    opacity: 0;
    left: 50%;
    top: 50%;
    transform: translateX(-50%) translateY(-50%) scale(0.2) rotateZ(15deg);
    display: none;
  }
}
</style>


