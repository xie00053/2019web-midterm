<template>
  <div class="testimonials">

    <!-- 将每次上传的comment打印到页面 loop comments-->
    <div class="list-group">
      <el-row :gutter="12" >
        <el-col :span="12" v-for="(comment,index) in comments" :key="index">
          <el-card shadow="always">            
              <span>{{comment}}</span>
          </el-card>
        </el-col>
      </el-row>
    </div>


    <!-- the form start from here -->
    <div class="userForm">
      <el-form :model="form" :rules="rules" ref="form">
        <h3>Leave us a testimonial</h3>
        <el-row>          
          <!-- First Name -->
          <el-form-item prop="yourName">
            <el-input placeholder="Your Name" v-model="form.yourName"></el-input>
          </el-form-item>
          
          <!-- position Title -->
          <el-form-item prop="position">
            <el-input placeholder="Position Title (no more than 30 words)" v-model="form.position"></el-input>
          </el-form-item>
          
          <!-- Description -->
          <el-form-item prop="desc">
            <el-input type="textarea" placeholder="Your Comments" v-model="form.desc"></el-input>
          </el-form-item>
        </el-row>
      </el-form>

      <!-- Submit button -->
      <el-button type="primary" @click="submitForm('form')">Submit</el-button>

    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {

  data () {
    return {    
        form: {
          yourName: null,
          position: null,
          desc: null,  
        },
        comments:[],

        // Rules for the form:--------
        // first name, last name, email, position can not be empty;
        // email should have the correct format; position can not more than 30 words.
        rules: {
          yourName:[
            {required: true, message: 'Please input Frist Name', trigger: 'blur'},
            { min:0, max: 30, message: 'You name cannot be more than 30 words', trigger: ['blur', 'change'] }
          ],
          position:[
            { required: true, message: 'Please input the position', trigger: 'blur' },
            { min:0, max: 30, message: 'Position title cannot be more than 30 words', trigger: ['blur', 'change'] }
          ],
          desc:[
            { required: true, message: 'Please input the comment', trigger: 'blur' },
            { min:0, max: 120, message: 'Comment cannot be more than 120 words', trigger: ['blur', 'change'] }
          ],
        }
    };
  },

  methods: {
      submitForm(form) {
        this.$refs[form].validate((valid) => {
          if (valid) {
            let userComment = this.form.yourName + '-' + this.form.position + '-' + this.form.desc
            // push the comments
            this.comments.push(userComment)
            
            // import axios to make api calls
            axios 
            // 链接到firebase，进入data.json, 加载comments
            .put("https://web-midterm.firebaseio.com/data.json", this.comments)
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
      .get("https://web-midterm.firebaseio.com/data.json")
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
</style>


