<template>
  <div class="navigation">
    <div class="navigation__logo">
      <!-- <img src="../../public/img/ADS_Lab.png" alt class="navigation__logo__icon" /> -->
      <img src="@/assets/img/ADS_Lab.png" alt class="navigation__logo__icon" />
    </div>

    <div class="navigation__shorten-icon" v-if="isphone">
      <input type="checkbox" class="navigation__checkbox" id="navi-toggle" v-model="isshow" />
      <label for="navi-toggle" class="navigation__button">
        <span class="navigation__icon"></span>
      </label>
    </div>

    <div class="navigation__nav" v-if="isshow2||!isphone" @click="nav_close()">
      <ul class="navigation__list" id="test">
      <div class="navigation__nav__logo"></div>

        <li
          v-for="(item, index) in links"
          :key="index"
          class="navigation__item"
          @click="change_num(index)"
        >
          <router-link
            class="navigation__link"
            :class="{active:index==num}"
            :to="links[index]"
          >{{item}}</router-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "navigation",
  data() {
    return {
      links: [ "home","grid", "author"],
      num: 0,
      isshow: false,
      isshow2: false,
      isphone: false,
      fullWidth: 0
    };
  },
  methods: {
    isshowfun() {},
    change_num(index) {
      this.num = index;
      this.isshow = false;
      this.isshow2 = false;
      window.scroll(0, 0);
    },
    nav_close() {
      this.isshow = false;
      var navigation__nav = document.getElementsByClassName("navigation__nav");
      var navigation__list = document.getElementsByClassName(
        "navigation__list"
      );
      for (let i = 0; i < navigation__list.length; i++) {
        let item = navigation__list[i];
        item.classList.add("moveright");
      }
      for (let i = 0; i < navigation__nav.length; i++) {
        let item = navigation__nav[i];
        item.classList.add("moveopacity");
      }
    }
  },
  watch: {
    fullWidth: function() {
      if (this.fullWidth <= 900) {
        this.isphone = true;
      } else {
        this.isphone = false;
      }
    },
    isshow: function() {
      if (this.isshow) {
        this.isshow2 = this.isshow;
      } else {
        setTimeout(() => {
          this.isshow2 = this.isshow;
        }, 500);
      }
    }
  },
  mounted() {
    const vm = this;
    vm.fullWidth = window.innerWidth;
    window.onresize = () => {
      vm.fullWidth = window.innerWidth;
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
