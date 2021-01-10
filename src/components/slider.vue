<template>
  <div class="slider">
    <div class="slider__container">
      <span class="slider__btn-left" @click="sliderClick(-1)">&lsaquo;</span>
      <span class="slider__btn-right" @click="sliderClick(1)">&rsaquo;</span>
      <div class="slider__btn-dots">
        <span @click="animatebot(1)"></span>
        <span @click="animatebot(2)"></span>
        <span @click="animatebot(3)"></span>
        <span @click="animatebot(4)"></span>
        <span @click="animatebot(5)"></span>
      </div>
      <div class="slider__imgs">
        <div>
          <img src="@/assets/img/gal-2.jpeg" alt="pure css slider" />
        </div>
        <div>
          <img src="@/assets/img/gal-1.jpeg" alt="pure css slider" />
        </div>
        <div>
          <img src="@/assets/img/gal-3.jpeg" alt="pure css slider" />
        </div>
        <div>
          <img src="@/assets/img/gal-4.jpeg" alt="pure css slider" />
        </div>
        <div>
          <img src="@/assets/img/gal-5.jpeg" alt="pure css slider" />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "slider",
  data() {
    return {
      list: null,
      dots: null,
      now_number: 1,
      timer: null
    };
  },
  methods: {
    animateFun(nowNumber) {
      let n = nowNumber;
      let pos = 2;
      let offsetWidth = this.list[0].offsetWidth;

      for (let i = 0; i < this.list.length; i++) {
        this.list[n].style.left = offsetWidth * pos + "px";
        if (pos == 0 || pos == 4) {
          this.list[n].style.zIndex = "0";
        } else if (pos == 1 || pos == 3) {
          this.list[n].style.zIndex = "1";
        } else {
          this.list[n].style.zIndex = "2";
        }
        n++;
        pos++;
        if (n > 4) {
          n = 0;
        }
        if (pos > 4) {
          pos = 0;
        }
      }
    },
    sliderClick(n) {
      clearInterval(this.timer);

      this.now_number += n;
      if (this.now_number == 6) {
        this.now_number = 1;
      } else if (this.now_number == 0) {
        this.now_number = 5;
      }
      this.animateFun(this.now_number - 1);
      this.sliderStart();
    },
    sliderStart() {
      this.timer = setInterval(() => {
        if (this.now_number == 5) {
          this.now_number = 1;
        } else {
          this.now_number++;
        }
        this.animateFun(this.now_number - 1);
      }, 3000);
    },
    animatebot(nowNumber) {
      clearInterval(this.timer);
      this.now_number = nowNumber;
      this.animateFun(this.now_number - 1);
      this.sliderStart();
    }
  },
  mounted() {
    this.list = document
      .getElementsByClassName("slider__imgs")[0]
      .getElementsByTagName("div");
    this.dots = document
      .getElementsByClassName("slider__btn-dots")[0]
      .getElementsByTagName("span");
    this.animateFun(this.now_number - 1);
    this.sliderStart();
    this.dots[this.now_number - 1].style = "background-color:rgba(0%, 0%, 0%, 0.5)";
    // window.console.log(this.list);
  },
  watch: {
    now_number() {
    //   window.console.log(this.now_number);
      for (let i = 0; i < this.dots.length; i++) {
        // window.console.log('color'+i);
        this.dots[i].style = "background-color:rgba(100%, 100%, 100%, 0.5)";
 
      }
        this.dots[this.now_number - 1].style = "background-color:rgba(0%, 0%, 0%, 0.5)";

    }
  }
};
</script>