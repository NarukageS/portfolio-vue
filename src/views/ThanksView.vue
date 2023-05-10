<template>
    <div>
        <transition name="fade">
            <div class="l_main" v-if="show">
                <div class="m_page-top">
                    <h2 class="m_page_title">送信完了</h2>
                    

                    <p class="contact_message">お問い合わせありがとうございます</p>
                </div>
                
            </div>
        </transition>
    </div>
</template>

<script>
export default {
    data() {
        return {
            show: false,
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

  .contact_message {
    font-size: 16px;
  }

</style>