
<template>
  <main class="l_main">
    <div class="l_container">
      <div class="u_flex">
        <div class="top_mv">
          <p class="top_mv_copy "><span class="js_kv_copy__1">Welcome</span> <span class="js_kv_copy__2">To</span> <span class="js_kv_copy__3">My Portforio</span></p>
          <v-vanta effect="waves" :options=options></v-vanta>
        </div>
        <div class="top_contents">
          <button class="top_contents_btn">
            <p>ABOUT</p>
            <img class="top_contents_btn-image" src="@/assets/icon/about.png" alt="">
          </button>
          <button class="top_contents_btn">
            <p>SKILL</p>
            <img class="top_contents_btn-image" src="@/assets/icon/skill.png" alt="">
          </button>
          <button class="top_contents_btn">
            <p>WORKS</p>
            <img class="top_contents_btn-image" src="@/assets/icon/works.png" alt="">
          </button>

        </div>
      </div>
      <div class="top_about_icon-wrapper">
        <div class="top_about_icon">
          <a href="https://twitter.com/N82436111" class="top_about_icon-link">
            <img width="50" height="50"
            src="@/assets//icon/twitter.png" alt="" class="top_about_icon-twitter">
          </a>
        </div>
        <div class="top_about_icon">
          <a href="https://www.facebook.com/profile.php?id=100080485482891" class="top_about_icon-link">
            <img width="50" height="50"
            src="@/assets/icon/facebook.png" alt="" class="top_about_icon-facebook">
          </a>
        </div>
        <div class="top_about_icon">
          <a href="https://github.com/NarukageS" class="top_about_icon-link">
            <img width="50" height="50"
            src="@/assets/icon/github.png" alt="" class="top_about_icon-facebook">
          </a>
        </div>
      </div>


      
      
    </div>
  </main>
</template>

<script>


export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.l_container {
  height: 85vh;

}
.u_flex {
  display: flex;
  margin: 0 10% ;
  height: 70vh;
  justify-content: space-between;
  align-items: center;
  
}

@media screen and (max-width:1080px) {
    .u_flex {
      flex-direction: column;
      justify-content: center;
    } 
}

.top_contents_btn {
  display: flex;
  align-items: center;
  gap: 48px;
  width: 300px;
  height: 60px;
  font-size: 32px;
  font-weight: bold;
  background-color: #F5F6FA;
  color: #fff;
  border-radius: 10px 40px 10px 40px;
  text-align: left;
  padding: 0 40px;
  letter-spacing: 0.5rem;
  transition: 0.5s;
}

.top_contents_btn-image {
  width: 64px;
  height: 64px;
  opacity: 0;
  transition: 0.5s;
}

.top_contents_btn:hover {
  width: 400px;
  height: 100px;
  color: #4D4D4D;
}

.top_contents_btn:hover .top_contents_btn-image {
  opacity: 1;
}

.top_mv_copy {
  font-size: 48px;
  font-weight: bold;
  white-space: nowrap;
}

@media screen and (max-width:1300px) {
    .top_mv_copy span {
      display: block;
    } 
}

@media screen and (max-width:1080px) {
    .top_mv_copy {
      text-align: center;
      font-size: 40px;
    } 
}


.top_contents {
  display: flex;
  flex-direction: column;
  gap: 32px;
  
}

@media screen and (max-width:1080px) {
    .top_contents {
      display: none;
    } 
}

.top_about_icon-wrapper {
  margin: 0 auto;
  width: 70vw;
  background-color: #F5F6FA;
  padding: 24px;
  justify-content: space-around;
  border-radius: 44px;
}

@media screen and (max-width:768px) {
    .top_about_icon-wrapper {
      width: 80vw;
      padding: 16px;
    }
}



</style>
