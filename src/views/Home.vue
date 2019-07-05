<template>
  <div class="home">
    <homepage msg="Welcome to My Vue App" />
  </div>
</template>


<script>
// @ is an alias to /src
import homepage from "@/components/homepage.vue";

export default {
  name: "home",
  components: {
    homepage
  }
};
</script>
