<template>
    <div id="single-blog">
        <h1>{{blog.title}}</h1>
        <article>{{blog.body}}</article>
    </div>
</template>

<script>
export default {
    name:"single-blog",
    data(){
        return{
            id:this.$route.params.id,
            blog:{}
        }
    },
    created(){
        //需要点击标题，可以展开页面的话，需要打开下面这段代码
    //     this.$http.get('https://jsonplaceholder.typicode.com/posts/'+this.id)
    //     .then(function(data){
    //         this.blog = data.body
    //     })
    }
}
</script>
<style >
 #single-blog{
     max-width:1000px;
     margin:0 auto ;
     text-align:center;
     background:#eee;
     border:1px solid #aaa;
 }
</style>