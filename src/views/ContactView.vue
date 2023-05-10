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
                <form action="https://docs.google.com/forms/u/0/d/e/1FAIpQLSeXTtCGdJtK4g8j-1MI2DVrEeBTEbCUXDAWt55tsKY7xe5eHA/formResponse" 
                target="hidden-iframe"
                class="contact_form">
                <dl class="contact_form_body">
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">お名前</dt>
                    <dd class="contact_form_unit-contents">
                        <input type="text" class="contact_form-input" name="entry.1903835591" v-model="form.name">
                    </dd>
                    </div>
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">電話番号</dt>
                    <dd class="contact_form_unit-contents">
                        <input type="tel" class="contact_form-input" name="entry.50365408" v-model="form.tel">
                    </dd>
                    </div>
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">メールアドレス</dt>
                    <dd class="contact_form_unit-contents">
                        <input type="text" class="contact_form-input" name="entry.268779276" v-model="form.email">
                    </dd>
                    </div>
                    <div class="contact_form_unit">
                    <dt class="contact_form_unit-head">お問い合わせ内容</dt>
                    <dd class="contact_form_unit-contents">
                        <textarea rows="6" class="contact_form-textarea" name="entry.282889568" v-model="form.text"></textarea>
                    </dd>
                    </div>
                </dl>
                <button type="submit" name="button" class="m_contact_button" @click="onSubmit">
                    送信する
                </button>
                <p class="error_message" v-if="error">※{{error}}</p>
                </form>
                
                <iframe name="hidden-iframe" style="display: none;"></iframe>
            </div>
        </transition>
    </div>
</template>

<script>
export default {
    data() {
        return {
            show: false,
            form: {
                name:"",
                tel:"",
                email:"",
                text:"",
            },
            
            error: ''
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
    methods: {
        onSubmit: function () {

            

            if (this.form.name.trim() === '') {
                this.error = 'お名前を入力してください'
                return
            }
            if (this.form.tel.trim() === '') {
                this.error = '電話番号を入力してください'
                return
            }
            if (this.form.email.trim() === '') {
                this.error = 'メールアドレスを入力してください'
                return
            }else if (!this.validEmail(this.form.email)) {
                this.error = 'メールアドレスを正しく入力してください';
            }
            if (this.form.text.trim() === '') {
                this.error = 'お問い合わせ内容を入力してください'
                return
            }

            if (this.error.trim() === '') {
                setTimeout(() => {
                    this.$router.push('/thanks');
                }, 1000);
                
            }
            //
        },
        validEmail: function (email) {
            var re = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
            return re.test(email);
        }
    },
    watch: {
        form: {
            handler: function() {
                this.error = '';
            },
            deep: true
        }
    }
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

  .error_message {
    color: red;
    margin-top: 16px;
    text-align: center;
  }

</style>