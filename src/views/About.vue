<template>
  <div class="about">
    <h1>This is an about page</h1>
    <Mosaic/>
  </div>
</template>

<script>
import Mosaic from "@/components/Mosaic.vue";
export default {
  components: {
    Mosaic
  },
  mounted(){
    document.getElementById("button").classList.add("buttom-hide")
  }
};
</script>
<style lang="scss">
.buttom-hide {
  display: none;
}
</style>


