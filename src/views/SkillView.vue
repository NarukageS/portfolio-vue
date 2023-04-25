<template>
<div>
    <transition name="fade">
        <div class="m_view_container" v-if="show">
            <div class="m_page-top">
            <h2 class="m_page_title">SKILL</h2>
            <p class="m_page_title-sub">スキル</p>
            </div>
            <div class="skill_content">
                <ul class="skill_list">
                    <li v-for="skill in skills" :key="skill.name" class="skill_item">
                        <img :src="skill.icon" alt="" class="skill_item_image">
                        <h3 class="skill_item_title">{{skill.name}}</h3>
                    </li>
                </ul>
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
            skills:[
                {
                    icon: require('@/assets/icon/html.png'),
                    name: "HTML"
                },
                {
                    icon: require('@/assets/icon/css.png'),
                    name: "CSS"
                },
                {
                    icon: require('@/assets/icon/sass.png'),
                    name: "Sass"
                },
                {
                    icon: require('@/assets/icon/js.png'),
                    name: "JavaScript"
                },
                {
                    icon: require('@/assets/icon/jquery.png'),
                    name: "jQuery"
                },
                {
                    icon: require('@/assets/icon/vue.png'),
                    name: "Vue.js"
                },
                {
                    icon: require('@/assets/icon/wp.png'),
                    name: "WordPress"
                },
                {
                    icon: require('@/assets/icon/xd.png'),
                    name: "Adobe Xd"
                },
            ]
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


    .m_view_container {
        height: 100vh;
    }

    .skill_content {
        max-width: 1080px;
        margin: 80px auto;
    }

    @media screen and (max-width:768px) {
        .skill_content {
            margin: 40px auto;
        } 
    }

    .skill_list {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 40px;
    }

    @media screen and (max-width:768px) {
        .skill_list {
            gap: 24px;
        } 
    }
    
    .skill_item {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 8px;
        width: calc(25% - 40px);
        height: 150px;
        background: #F5F6FA;
        border-radius: 20px;
    }

    @media screen and (max-width:1080px) {
        .skill_item {
        width: calc(30% - 40px);
        } 
    }

    @media screen and (max-width:768px) {
        .skill_item {
        width: calc(45% - 40px);
        } 
    }

    @media screen and (max-width:500px) {
        .skill_item {
        width: calc(50% - 40px);
        } 
    }

    .skill_item_image {
        width: 80px;   
        height: 80px;
    }

    @media screen and (max-width:1080px) {
        .skill_item_image {
            width: 60px;   
            height: 60px;
        }
    }

    @media screen and (max-width:500px) {
        .skill_item_image {
            width: 40px;   
            height: 40px;
        }
    }

    .skill_item_title {
        font-weight: bold;
    }
</style>