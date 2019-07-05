<template>
<!-- this is the Home page -->
  <div class="home">
    <!-- this msg from the component homepage -->
    <h1>{{ msg }}</h1>

    <el-col :span="12">
      <el-image :src="homeSrc"></el-image>
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
      homeSrc: require ('../assets/homevue.jpg'),
      homepageP1: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ut orci eu nibh pulvinar finibus sodales sed arcu. Maecenas commodo congue elit non pulvinar. Vivamus faucibus, odio at accumsan luctus, ex leo convallis sapien, id euismod purus libero et ipsum. Donec ullamcorper pharetra sapien, sit amet ullamcorper nibh aliquet in. Praesent porta vulputate faucibus. Donec commodo urna purus, a consectetur arcu varius eu. Quisque quam mauris, tempus non urna a, accumsan fringilla massa. Suspendisse dapibus sit amet nibh ut dictum. Maecenas at odio erat. Donec at sapien vel tellus condimentum venenatis at a diam. Suspendisse pharetra ligula nibh. Nullam sit amet accumsan purus, non porttitor neque. Vivamus vel bibendum odio.',
    }
  },
  
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.home .el-image {
  width:90%;
}

</style>
