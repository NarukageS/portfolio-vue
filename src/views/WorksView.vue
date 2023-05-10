<template>
    <div>
        <transition name="fade">
            <div class="m_view_container" v-if="show">
                <div class="m_page-top">
                <h2 class="m_page_title">WORKS</h2>
                <p class="m_page_title-sub">実績</p>
                </div>
                <div class="works_content">
                    <h3 class="works_content_title">制作実績</h3>
                    <ul class="works_content_items">
                        <li class="works_content_item"
                        v-for="(work,index) in works"
                        :key="work.name"
                        @mouseover="mouseOver(index)"
                        @mouseleave="mouseLeave(index)"
                        >
                        
                            <button @click="modalOpen">
                                <img :src="work.image" alt="">
                                <transition name="hover">
                                <h4 
                                class="works_gallery_item-title"
                                v-show="hover && index === hoverIndex"
                                >{{work.name}}</h4>
                                </transition>
                                <transition name="hover">
                                <div v-show="hover && index === hoverIndex" class="dark-cover"></div>
                                </transition>
                            </button>
                            <transition name="modal">
                            <modal-window 
                            class="modal_window"
                            v-show="modal && index === hoverIndex" 
                            :url="work.image"
                            :name="work.name"
                            :overview="work.overview"
                            :period="work.period"
                            :ingenuity="work.ingenuity"
                            :skill="work.skill"
                            :link="work.link"
                            @is-close="modal = $event"/>
                            </transition>
                        </li>
                    </ul>
                    
                </div>
                <!-- <div class="works_content works_content__portfolio-history">
                    <div class="">
                        <h3 class="works_content_title works_content_title__portfolio-history">ポートフォリオの歴史</h3>
                        <ul class="works_content_items">
                            <li class="works_content_item"
                            v-for="(version,index) in versions"
                            :key="version.name"
                            @mouseover="mouseOver(index)"
                            @mouseleave="mouseLeave(index)"
                            >
                                <button @click="modalOpen">
                                    <img :src="version.image" alt="">
                                    <transition name="hover">
                                    <h4 
                                    class="works_gallery_item-title"
                                    v-show="hover && index === hoverIndex"
                                    >{{version.name}}</h4>
                                    </transition>
                                    <transition name="hover">
                                    <div v-show="hover && index === hoverIndex" class="dark-cover"></div>
                                    </transition>
                                </button>
                                <transition name="modal">
                                <modal-window 
                                class="modal_window"
                                v-show="modal" 
                                :url="version.image"
                                :name="version.name"
                                :overview="version.overview"
                                :period="version.period"
                                :ingenuity="version.ingenuity"
                                :skill="version.skill"
                                @is-close="modal = $event"/>
                                </transition>
                            </li>
                        </ul>
                    </div>
                </div> -->
            </div>
        </transition>
    </div>
</template>

<script>
import modalWindow from "@/components/modalWindow"

export default {
  components: { modalWindow },
    component: {
        modalWindow
    },
    data() {
        return {
            show:false,
            hover:false,
            hoverIndex: null,
            modal: false,
            works:[
                {
                    name:"ポートフォリオver1",
                    image: require('@/assets/work01.jpg'),
                    overview:"1ページ、レスポンシブ対応、CMS化（WordPress）",
                    period:"１ヶ月半",
                    ingenuity:"モノクロのシンプルなデザインにしてアニメーションで少し遊びました。",
                    skill:"HTML、CSS、JS、jQuery、WordPress",
                    link: 'https://naru-portfolio.com/'
                },
                {
                    name:"鳳来弁当 様",
                    image: require('@/assets/work02.jpg'),
                    overview:"1ページ、レスポンシブ対応",
                    period:"１ヶ月",
                    ingenuity:"素のJSで全てのアニメーションを作成しました。",
                    skill:"HTML、CSS、JS",
                    link: 'https://houraibentou.web.fc2.com/'
                },
                {
                    name:"ポートフォリオver2",
                    image: require('@/assets/work03.jpg'),
                    overview:"5ページ、レスポンシブ対応、SPA",
                    period:"１ヶ月",
                    ingenuity:"ポートフォリオをSPAにしました。",
                    skill:"HTML、CSS、Vue.js",
                    link: 'https://version2.naru-portfolio.com/'
                },
                
            ],
            versions: [
                
            ]
        }
    },
    methods:{
        mouseOver(index){
            this.hover = true;
            this.hoverIndex = index
        },
        mouseLeave(){
            this.hover = false;
        },
        modalOpen() {
            this.modal = true
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
    .hover-enter-active, .modal-enter-active {
    transition: 0.5s;
    opacity: 0;
  }
  .hover-enter-to, .modal-enter-to {
    opacity: 1;
  }

  .hover-leave-active, .modal-leave-active {
    transition: 0.5s;
    opacity: 1;
  }

  .hover-leave-to, .modal-leave-to {
    opacity: 0;
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

    .m_view_container {
        height: 100vh;
    }

    .works_content {
        margin: 40px 0;
        padding: 24px 0;
    }

    @media screen and (max-width:768px) {
        .works_content {
            margin: 32px 0;
            padding: 16px 0;
        }
    }

    .works_content__portfolio-history {
        background: #4d4d4d;
    }

    .works_content_title {
        font-size: 20px;
        font-weight: bold;
        text-align: center;
        padding: 8px 0;
    }

    .works_content_title__portfolio-history {
        color: #fff;
    }

    .works_content_items {
        display: flex;
        justify-content: space-around;
        margin-top: 40px;
        gap: 40px;
        align-items: center;
        flex-wrap: wrap;
    }

    .works_content_item {
        width: 300px;
        position: relative;
    }


    .works_content_item img {
        border: #4d4d4d 1px solid;
        border-radius: 10px 40px 10px 40px;
    }

    .works_gallery_item-title {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        color: #4d4d4d;
        font-weight: bold;
        z-index: 2;
        font-size: 16px;
    }

    .dark-cover {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        z-index: 1;
        /* opacity: .8; */
        background-color: #F5F6FA;
        border-radius: 9px 36px 9px 36px;
    }

    .works_content_item-title {
        font-size: 16px;
        font-weight: bold;
    }

    .modal_window {
        position: fixed;
        z-index: 50;
    }
</style>