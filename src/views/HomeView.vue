<template>
<div>
  <transition name="fade">
    <div class="home" v-if="show">
      <HelloWorld msg="Welcome to Your Vue.js App" />
      <contact-section />
    </div>
  </transition>
</div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import contactSection from '@/components/contactSection'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    contactSection
  },
  data() {
    return {
      show: false
    }
  },
    mounted() {
      //コンポーネントがマウントされるタイミングでフラグを書き換え->表示アニメーション
      this.show = true;
    },
    beforeRouteLeave(to, from, next) {
      //vue-routerでの遷移発生イベント時にフラグを書き換え->削除アニメーション
      this.show = false;
      setTimeout(() => {
        //setTimeoutにより、3秒後にページ遷移を実行
        next();
      }, 1000);
    },
}
</script>
<style scoped>
  .fade-enter-active {
    transition:  1.5s;
    transform: translateY(100px);
    opacity: 0;
  }
  .fade-enter-to {
    transform: translateY(0px);
    opacity: 1;
  }

  .fade-leave-active {
    transition: 1.5s;
    transform: translateY(0px);
    opacity: 1;
  }
  .fade-leave-to {
    transform: translateY(100px);
    opacity: 0;
  }

</style>