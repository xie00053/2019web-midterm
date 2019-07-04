<template>
  <div class="contact">
    <h1>{{title}}</h1>
    <el-row>
      <el-col :span="12">
        <h3>{{addressName}}</h3>
        <p>{{addressText}}</p>
      </el-col>
      <el-col :span="12">
        <h3>{{hourTitle}}</h3>
        <!-- loop for open hours -->
        <dt v-for="(value, name) in openHours" :key="name">{{name}} : {{value}}</dt>        
      </el-col>
    </el-row>
    <p></p>
  </div>
</template>


<script>
export default {
  name: "contact",

  data () {
    return {
      title: 'Contact',
      addressName:'Address',
      addressText:`1435 Woodroffe Avenue, Ottawa,Ontario. K2G1V8 613-7274723`,
      hourTitle:'Hours of Operation',
      openHours: {
        Monday:    '8AM-6PM',
        Tuesday:   '8AM-6PM',
        Wednesday: '8AM-6PM',
        Thursday:  '8AM-6PM',
        Friday:    '8AM-5PM',
        Saturday:  '10AM-4PM',
        Sunday:    '10AM-2PM',
      },    
    }
  },

  
}
</script>
<style scoped>
p {
  width:50%;
}
</style>
