<template>
  <div id="blog">
<h2>WELCOME TO MY NEW BLOG </h2>
<form>
  <label>Blog Title:</label>
  <input type="text" v-model="blog.title" required/>
  <label> Author: </label>
  <input type="text" v-model="blog.author" required/>
  <label>Content in the Blog:</label>
  <textarea v-model="blog.content"></textarea>
  <h4>Programming Languages</h4>
  <div id="checkboxes">
    <label>HTML</label>
    <input type="checkbox" value="HTML" v-model="blog.categories"/>
    <label>CSS</label>
    <input type="checkbox" value="CSS" v-model="blog.categories"/>
    <label>JAVA SCRIPT</label>
    <input type="checkbox" value="JAVA SCRIPT" v-model="blog.categories"/>
    <label>VUE.JS</label>
    <input type="checkbox" value="VUE.JS" v-model="blog.categories"/>
  </div>
  <button v-on:click.prevent="post">Add Blog</button>
</form>
<div id="preview">
  <h3>Blog preview</h3>
  <p>Blog Title: {{blog.title}}</p>
  <p>Author: {{blog.author}}</p>
  <p>Content in the Blog:</p>
  <p>{{blog.content}}</p>
  <p>Blog Categories:</p>
  <p>{{blog.categories}}</p>
  </div>
  </div>
</template>
<script>
export default {
  data(){
    return{
      blog:{
      title: "",
      content: "",
      categories:[],
      },
      methods:{
        post: function(){
          this.$http.post('http://jsonplaceholder.typicode.com/posts',{
            title:this.blog.title,
            body:this.blog.content,
            userid: 1
          }).then(function(data ){
            console.log(data);
          });
        }

      }
    }
  }
}
</script>
<style>
#add-blog*{
  box-sizing: border-box;
}
#add-blog {
  margin: 20px auto;
  max-width: 40px;
}
label{
  display: block;
  margin: 20px 0 10px;
}
input[type="text"],textarea{
  display: block;
  width: 50%;
  padding: 8px;
}
#preview{
  padding: 10px 20px;
  border: 1px dotted #ccc;
  margin: 30px 0;
}
h3{
  margin-top: 50px;
}
#checkboxes input{
  display: inline-block;
  margin-right:50px ;
}
#checjboxes label{
  display: inline-block;
}
</style>
