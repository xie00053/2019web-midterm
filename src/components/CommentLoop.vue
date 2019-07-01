<template>
    <div class="list-group">
      <el-row :gutter="12" >
        <el-col :span="12" v-for="(comment,index) in commentsList" :key="index">
          <el-card shadow="always">            
              <span @click="commentDone(index)">{{comment}}</span>
          </el-card>
        </el-col>
      </el-row>
    </div>
</template>

<script>
export default {
  // 添加props方式1: 
  // props: ['commentsList'],
  // 方法2: 给props添加条件，比如这里要求props的内容必须是array,
  props: {
    commentsList:{
        type: Array,
        required: true,
    }
  },

  methods: {
    commentDone(index) {
      console.log(index);
      this.$emit("removeComment", index)
    }
  }
}
</script>

<style scoped>
  .el-card {
      margin-bottom: 1.5rem;
      background-color: #ffffff;
    }
</style>
