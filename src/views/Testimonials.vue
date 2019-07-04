<template>
  <div class="testimonials">

    <!-- loop comments 将每次上传的comment打印到页面 -->
    <CommentLoop :commentsList="comments" @removeComment="appDeleteTodo"/>


    <!-- the form start from here -->
    <div class="userForm">
      <el-form :model="form" :rules="rules" ref="form">
        <h3>Leave us a testimonial</h3>
        <el-row>          
          <!-- First Name -->
          <el-form-item prop="yourName">
            <el-input placeholder="Your Name (no more than 50 words)" v-model="form.yourName"></el-input>
          </el-form-item>
          
          <!-- position Title -->
          <el-form-item prop="position">
            <el-input placeholder="Position Title (no more than 50 words)" v-model="form.position"></el-input>
          </el-form-item>
          
          <!-- Description -->
          <el-form-item prop="desc">
            <el-input type="textarea" placeholder="Your Comments (no more than 50 words)" v-model="form.desc"></el-input>
          </el-form-item>
        </el-row>
      </el-form>

      <!-- Submit button -->
      <el-button type="primary" @click="submitForm('form')">Submit</el-button>

    </div>
  </div>
</template>

<script>
// import component CommentLoop
import CommentLoop from "@/components/CommentLoop.vue";
import axios from 'axios'

export default {

  components: {
    CommentLoop,
  },

  data () {
    return {    
        form: {
          yourName: null,
          position: null,
          desc: null,  
        },
        comments:[],

        // Rules for the form:--------
        // name, position, comment desc can not be empty;
        // name, position title can not more than 30 words, comment desc can not more than 120 words.
        rules: {
          yourName:[
            {required: true, message: 'Please input Frist Name', trigger: 'blur'},
            { min:0, max: 50, message: 'You name cannot be more than 50 words', trigger: ['blur', 'change'] }
          ],
          position:[
            { required: true, message: 'Please input the position', trigger: 'blur' },
            { min:0, max: 50, message: 'Position title cannot be more than 50 words', trigger: ['blur', 'change'] }
          ],
          desc:[
            { required: true, message: 'Please input the comment', trigger: 'blur' },
            { min:0, max: 120, message: 'Comment cannot be more than 120 words', trigger: ['blur', 'change'] }
          ],
        }
    };
  },


  methods: {
        
    appDeleteTodo(index) {
      // delete comment card
      this.comments.splice(index, 1);
        axios.put(
        "https://vue-and-axios.firebaseio.com/data.json",
        this.comments
        );
    },

    submitForm(form) {
      this.$refs[form].validate((valid) => {
        if (valid) {
          let userComment = this.form.yourName + '-' + this.form.position + this.form.desc
          // push the comments
          this.comments.push(userComment)
          
          // import axios to make api calls
          axios 
          // 链接到firebase，进入data.json, 加载comments
          .put("https://xie00053-vue-and-axios.firebaseio.com/data.json", this.comments)
          // 检测如果 .put 通过的话，运行.then
          .then(response => {
              console.log(response);
              console.log("Your data was saved status:" + response.status)
          })

          // 检测如果 .put 没有通过的话，运行.catch
          .catch(error => {
              console.log(error);
          })


          // reset the form
          this.$refs[form].resetFields();
        } else {
          console.log('error submit!!');
          return false;
        }    
      });
    },
  },

// created is a life cycle hook which will run when the instance is created
  created() {
      
  // here we are making a GET request using AXIOS to get the data
  axios
    .get("https://xie00053-vue-and-axios.firebaseio.com//data.json")
    .then(response => {
      // console.log(response);
      // console.log(response.data);
      // Checking if the response has some data
      if (response.data) {
        this.comments = response.data;
      }
    })
    .catch(error => {
      console.log("There was an error in getting data: " + error.response);
    });
  }
}
</script>

<style scoped>
  .userForm{
    border: 1px solid black;
    padding: 2rem;
  }
  .el-row{
    margin-bottom: 1.5rem;
  }

  .el-card {
    margin-bottom: 1.5rem;
    background-color: #ffffff;
  }
</style>


