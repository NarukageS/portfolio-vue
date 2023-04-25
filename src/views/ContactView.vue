<template>
    <div>
        <transition name="fade">
            <div class="l_main" v-if="show">
                <div class="m_page-top">
                <h2 class="m_page_title">CONTACT</h2>
                <p class="m_page_title-sub">お問い合わせ</p>

                <p class="contact_message">ご依頼、ご相談、お見積もりなど <br>
                    お気軽にお問い合わせください</p>
                </div>
                <form action="" class="contact_form">
                <dl class="contact_form_body">
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">お名前</dt>
                    <dd class="contact_form_unit-contents">
                        <input type="text" class="contact_form-input">
                    </dd>
                    </div>
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">電話番号</dt>
                    <dd class="contact_form_unit-contents">
                        <input type="email" class="contact_form-input">
                    </dd>
                    </div>
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">メールアドレス</dt>
                    <dd class="contact_form_unit-contents">
                        <input type="email" class="contact_form-input">
                    </dd>
                    </div>
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">お問い合わせ内容</dt>
                    <dd class="contact_form_unit-contents">
                        <textarea rows="6" class="contact_form-textarea"></textarea>
                    </dd>
                    </div>
                </dl>
                <button class="m_contact_button">
                    送信する
                </button>
                </form>
                
            </div>
        </transition>
    </div>
</template>

<script>
export default {
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

<style>
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