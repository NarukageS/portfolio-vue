<template>
  <header class="l_header js_header">
    <div class="l_header_inner" :class="{'is-active': lineActive}">
      <h1 class="l_header_logo"><router-link to="/"><i>SHUNYA<br>NARUKAGE</i></router-link></h1>

      <nav class="l_header_nav js_navigation" :class="{is_active: isActive}">
        <ul class="l_header_list">
          <li class="l_header_item" @click="isActive = false">
            <router-link to="/" class="l_header_link">
              <span>H</span><span>O</span><span>M</span><span>E</span>
            </router-link>
          </li>
          <li class="l_header_item" @click="isActive = false">
            <router-link to="/about" class="l_header_link">
              <span>A</span><span>B</span><span>O</span><span>U</span><span>T</span>
            </router-link>
          </li>
          <li class="l_header_item" @click="isActive = false">
            <router-link to="/skill" class="l_header_link">
              <span>S</span><span>K</span><span>I</span><span>L</span><span>L</span>
            </router-link>
          </li>
          <li class="l_header_item" @click="isActive = false">
            <router-link to="/works" class="l_header_link">
              <span>W</span><span>O</span><span>R</span><span>K</span><span>S</span>
            </router-link>
          </li>
          <li class="l_header_item" @click="isActive = false">
            <router-link to="/contact" class="l_header_link">
              <span>C</span><span>O</span><span>N</span><span>T</span><span>A</span><span>C</span><span>T</span>
            </router-link>
          </li>
        </ul>
      </nav>

      <button class="m_hamburger js_hamburger" :class="{is_active: isActive}" @click="isActive = !isActive">
        <div class="m_hamburger-bar"></div>
        <div class="m_hamburger-bar"></div>
        <div class="m_hamburger-bar"></div>
      </button>

    </div>
  </header>
</template>

<script>
export default {
    data() {
        return {
            isActive: false,
            lineActive: false
        }
    },
    methods: {
        scrollWindow() {
            const top = 100 //topから100pxスクロールしたらボタン登場
            this.scroll = window.scrollY //垂直方向
            if (top < this.scroll) {
                this.lineActive = true
            } else {
                this.lineActive = false
            }
        } 
    },
    mounted() {
        window.addEventListener('scroll',this.scrollWindow)
    },
    
}
</script>

<style scoped>

</style>