<template>
  <div class="wrapperHeader">
    <div class="header shadow-5" :style="{ backgroundImage: 'url(/images/' + image + ')' }">
    </div> 
  </div>
</template>

<script>
export default {
  props: {
    image: {
      type: String,
      required: true
    }
  }
}
</script>

<style>
.wrapperHeader {
  padding-bottom: 30px;
}

.wrapperHeader .header {
  height:170px;
  margin:0 auto;
  width: 100%;
  background-position: center; 
  text-align: center;
}
</style>
