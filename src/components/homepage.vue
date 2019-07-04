<template>
  <div class="home">
    <h1>{{ msg }}</h1>
    <el-col :span="12">
    <img alt="Vue logo" src="../assets/homevue.jpg" />
    </el-col>
    <el-col :span="12">
    <p>{{ homepageP1 }}</p>
    </el-col>
  </div>
</template>

<script>
export default {
  name: "homepage",
  props: {
    msg: String
  },

  data () {
    return {
      homepageP1: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ut orci eu nibh pulvinar finibus sodales sed arcu. Maecenas commodo congue elit non pulvinar. Vivamus faucibus, odio at accumsan luctus, ex leo convallis sapien, id euismod purus libero et ipsum. Donec ullamcorper pharetra sapien, sit amet ullamcorper nibh aliquet in. Praesent porta vulputate faucibus. Donec commodo urna purus, a consectetur arcu varius eu. Quisque quam mauris, tempus non urna a, accumsan fringilla massa. Suspendisse dapibus sit amet nibh ut dictum. Maecenas at odio erat. Donec at sapien vel tellus condimentum venenatis at a diam. Suspendisse pharetra ligula nibh. Nullam sit amet accumsan purus, non porttitor neque. Vivamus vel bibendum odio.',
    }
  },
  
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.home img {
  width:90%;
}

</style>
