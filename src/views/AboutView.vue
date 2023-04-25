<template>
  <div>
    <transition name="fade">
      <div v-if="show">
        <div class="m_page-top" >
          <h2 class="m_page_title">ABOUT</h2>
          <p class="m_page_title-sub">私について</p>
        </div>
        <section class="top_about top_section" id="1">
            <div class="l_content">
              <h2 class="top_section_title js_section_title">
                PROFILE
              </h2>
              <div class="top_about_inner js_about">
                <div class="top_about_img-wrapper">
                  <img 
                  width="1478"
                  height="1108"
                  src="@/assets/about.jpg" 
                  alt="" 
                  class="top_about_img">
                </div>
                <div class="top_about_text">
                  <table class="top_about_table">
                    <tr class="top_about_table-tr">
                      <th class="top_about_table-th">氏名：</th>
                      <td class="top_about_table-td">成影俊也（ナルカゲシュンヤ）</td>
                    </tr>
                    <tr class="top_about_table-tr">
                      <th class="top_about_table-th">出身：</th>
                      <td class="top_about_table-td">京都、現在は都内在住</td>
                    </tr>
                    <tr class="top_about_table-tr">
                      <th class="top_about_table-th">趣味：</th>
                      <td class="top_about_table-td">読書、投資</td>
                    </tr>
                  </table>
                  <p class="top_about_desc">都内のITベンチャーで勤務しています。<br>
                    Web制作や広告、マーケティングについて
                    <br>日々学習しております。
                    <span class="top_about_desc__line">
                    相談事がございましたら、ご遠慮なくお申し付けください。
                    </span>
                    </p>
                    <div class="top_about_icon-wrapper">
                      <div class="top_about_icon">
                        <a href="" class="top_about_icon-link">
                          <img width="50" height="50"
                          src="@/assets//icon/twitter.png" alt="" class="top_about_icon-twitter">
                        </a>
                      </div>
                      <div class="top_about_icon">
                        <a href="" class="top_about_icon-link">
                          <img width="50" height="50"
                          src="@/assets/icon/facebook.png" alt="" class="top_about_icon-facebook">
                        </a>
                      </div>
                    </div>
                </div>
                
              </div>
            </div>
          </section>
          <section class="top_policy top_section" id="2">
            <div class="l_content">
              <h2 class="top_section_title js_section_title">POLICY</h2>
              <div class="top_policy_inner js_policy">
                <div class="top_policy_content js_policy_content">
                  <p class="top_policy_content-item">迅速なレスポンス</p>
                  <p class="top_policy_content-desc">ご連絡を確認次第すぐ（遅くとも24時間以内）に返信することをお約束いたします。</p>
                </div>
                <div class="top_policy_content js_policy_content">
                  <p class="top_policy_content-item">責任をもってやり遂げる</p>
                  <p class="top_policy_content-desc">責任感を持ち、保守・修正まで意識したコーディングをします。</p>
                </div>
                <div class="top_policy_content js_policy_content">
                  <p class="top_policy_content-item">前進し続ける</p>
                  <p class="top_policy_content-desc">常に向上心を持って、新たな知識・スキルの習得を継続していきます。</p>
                </div>
              </div>
            </div>
          </section>
          <contact-section />
        </div>
      </transition>
  </div>
</template>

<script>
import contactSection from '@/components/contactSection'

export default {
  components: {
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

<style>
  @media screen and (max-width:1080px) {
    .top_about_icon {
      width: 32px;
    } 
  }
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
