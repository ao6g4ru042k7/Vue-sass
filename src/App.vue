<template>
  <div id="app">
    <div id="nav">
      <Navigation />
    </div>
    <div id="section">
      <router-view />
    </div>
    <div id="footer">
      <Footer />
    </div>
  </div>
</template>

<script>
import Navigation from "@/components/navigation.vue";
import Footer from "@/layout/footer.vue";

export default {
  components: {
    Navigation,
    Footer
  }
};
</script>
<style lang="scss">
//載入Google字體
@import url("https://fonts.googleapis.com/css?family=Noto+Sans+TC|Nunito|Josefin+Sans:300,400,400i&display=swap");

//載入自訂SCSS
@import "assets/sass/main.scss";

@import "assets/img/font-awesome/css/fontawesome.min.css";
#nav {
  z-index: 9999;
  width: 100%;
  height: 6rem;
  position: fixed;
  top: 0;
  left: 0;
}
#section {
  position: relative;
  top: 6rem;
}
#footer {
  position: relative;
  top: 6rem;
  font-size: 10rem;
}
</style>
