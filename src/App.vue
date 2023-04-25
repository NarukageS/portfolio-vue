<template>
  <now-loading v-if="loadingActive"/>
  <div v-if="!loadingActive">
    <header-component />
    <router-view/>
  </div>
  <!-- <footer-component /> -->
</template>
<script>
import headerComponent from '@/components/headerComponent'
import nowLoading from '@/components/nowLoading'
// import footerComponent from '@/components/footerComponent'
export default {
  components: {
    headerComponent,
    nowLoading
    // footerComponent,
  },
  data() {
    return {
      loadingActive: true
    }
  },
  methods:{
      loadingOff(){
          this.loadingActive = false;
      }
  },
  mounted(){
      setTimeout(this.loadingOff,2000);
  }
}
</script>


<style>

</style>
