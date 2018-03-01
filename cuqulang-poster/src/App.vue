<template>
  <div>
    <page></page>
    <footerBottom></footerBottom>
  </div>
  
</template>
<script>
import Hello from './components/Hello'
import page from './components/main-page'
import footerBottom from './components/footer'

export default {
  name: 'carrousel',
  components: {
    page,
    footerBottom
  },
  directives: {
    focus: {
      inserted: function(el){
        // debugger;
        el.focus()
      }
    }
  },
  data() {
    return {

    }
  }
}
</script>

<style lang="scss">
body, html, #app {
  font-family: 'Microsoft YaHei', 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.swiper-button-prev {
  left: 50px;
}
.swiper-button-next {
  right: 50px;
}

.swiper-container-horizontal > .swiper-pagination-bullets {
  width: 30%;
  left: 35%;
  bottom: 30px;
}
.swiper-pagination {
  background-color: #000;
  background-color: rgba(0, 0, 0, .5);
  // opacity: .5;
  border-radius: 30px;
  width: 30%;
  padding: 8px 0;
}
.swiper-slide {
         overflow-y: scroll;
        -webkit-overflow-scrolling: touch;
    }
.my-span {
  margin: 0 10px;
  width: 14px;
  height: 14px;
  line-height: 20px;
  font-size: 12px;
  opacity: 1;

  display: inline-block;
  border-radius: 100%;
  background: #fff;
  opacity: .5;
}
.swiper-pagination-bullet-active.my-span {
  opacity: 1;
}
</style>
