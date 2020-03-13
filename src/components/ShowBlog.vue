<template>
  <div id="show-blog" v-theme:column=" 'narrow' ">
  <h1 >博客总览</h1>
  <input type="text" v-model="search" placeholder="搜索">
  <div v-for="blog in filteredBlogs" :key="blog.index"  class="single-blog">
    <router-link v-bind:to="'/blog/'  +blog.id"><h2 v-rainbow>{{blog.title}}</h2></router-link>  
      <article>
          {{blog.body}}
      </article>
  </div>
  </div>
</template>

<script>


export default {
    name: 'show-blog',
    data(){
        return{
            blogs:[],
            search:""
        }
    },
    created(){
         //需要点击标题，可以展开页面的话，需要打开下面这段代码
        // this.$http.get("https://jsonplaceholder.typicode.com/posts/")
        this.$http.get("./../static/posts.json")
        .then(function(data){
            // console.log(data);
            this.blogs = data.body
            console.log(this.blogs)
        })
    },
    computed:{
        filteredBlogs:function(){
            return this.blogs.filter((blog) => {
                return blog.title.match(this.search);
            })
        }
    }
}
</script>

<style scoped>
#show-blog{
    max-width:800px;
    margin:0 auto;
}
.single-blog{
    padding:20px;
    margin:20px 0;
    box-sizing:border-box;
    background: #eee;
    border:1px dotted #aaa;
}
#show-blog a{
    color:#444;
    text-decoration: none;
}
input[type="text"]{
    padding:8px;
    width:100%;
    box-sizing:border-box;
}
</style>
