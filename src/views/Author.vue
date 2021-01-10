<template>
  <div class="author">
      <!-- <Header/> -->
      <Section1/>
      <!-- <Section2/> -->
      <!-- <Section3/> -->
  </div>
</template>

<script>
// @ is an alias to /src
// import Header from '@/views/home/header.vue'
import Section1 from '@/views/author/section-1.vue'
// import Section2 from '@/views/grid/section-2.vue'
// import Section3 from '@/views/grid/section-3.vue'

export default {
  name: 'author',
  components: {
    // Header,
    Section1,
    // Section2,
    // Section3
  }
}
</script>
<style lang="scss">
  .author{
    display: grid;
    grid-template-rows: min-content min-content min-content;
    // grid-template-columns: [full-start] minmax(4rem,8rem)[center-start] repeat(8,[col-start] minmax(min-content,14rem) [col-end])[center-end] minmax(4rem,8rem)[full-end]
  }
</style>