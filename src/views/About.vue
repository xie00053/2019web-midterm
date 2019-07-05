<template>
<!-- the About page -->

  <div class="about">

    <h1>{{ title }}</h1>

    <!-- The first row  -->
    <el-row>
      <el-col :span="8">
        <el-image :src="aboutSrc"></el-image>
      </el-col>
      <el-col :span="16">
        <p>{{ aboutP1 }}</p>
      </el-col>
    </el-row>

    <!-- The second row  -->
    <el-row>
      <el-col :span="16">
        <p>{{ aboutP2 }}</p>
      </el-col>
      <el-col :span="8">
        <el-image :src="aboutSrc"></el-image>
      </el-col>
    </el-row>

  </div>
</template>

<script>
export default {
  name: "about",

  data () {
    return {
      aboutSrc: require ('../assets/logo1.jpg'),
      title: 'About the Vue App',
      aboutP1: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ut orci eu nibh pulvinar finibus sodales sed arcu. Maecenas commodo congue elit non pulvinar. Vivamus faucibus, odio at accumsan luctus, ex leo convallis sapien, id euismod purus libero et ipsum. Donec ullamcorper pharetra sapien, sit amet ullamcorper nibh aliquet in. Praesent porta vulputate faucibus. Donec commodo urna purus, a consectetur arcu varius eu. Quisque quam mauris, tempus non urna a, accumsan fringilla massa. Suspendisse dapibus sit amet nibh ut dictum. Maecenas at odio erat. Donec at sapien vel tellus condimentum venenatis at a diam. Suspendisse pharetra ligula nibh. Nullam sit amet accumsan purus, non porttitor neque. Vivamus vel bibendum odio.',
      aboutP2: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin ut orci eu nibh pulvinar finibus sodales sed arcu. Maecenas commodo congue elit non pulvinar. Vivamus faucibus, odio at accumsan luctus, ex leo convallis sapien, id euismod purus libero et ipsum. Donec ullamcorper pharetra sapien, sit amet ullamcorper nibh aliquet in. Praesent porta vulputate faucibus. Donec commodo urna purus, a consectetur arcu varius eu. Quisque quam mauris, tempus non urna a, accumsan fringilla massa. Suspendisse dapibus sit amet nibh ut dictum. Maecenas at odio erat. Donec at sapien vel tellus condimentum venenatis at a diam. Suspendisse pharetra ligula nibh. Nullam sit amet accumsan purus, non porttitor neque. Vivamus vel bibendum odio.',
    }
  },
  
};
</script>

<style>
.about img{
  width:80%;
  margin-bottom: 1.5rem;
}
</style>

