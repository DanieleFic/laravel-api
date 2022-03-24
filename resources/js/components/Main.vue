<template>
    <div>
        <ul>
            <li v-for="(post, index) in posts" :key="index">
                <h1>post</h1>
                <h4>Titolo:</h4>{{post.title}}
                <h4>Autore</h4>{{post.author}}
                <h4>Contenuto:</h4>{{post.content}} 
                <h4>Categoria:</h4>
                <p >{{post.category ? post.category.name : "nessuna categoria" }}</p>
                <h4>Tag:</h4>
                <div v-if="post.tags != null ">
                    <p v-for="(tag, index) in post.tags" :key="index"  >
                    {{ tag.name }}
                </p>
                </div>
                <div v-else>
                    <p> no tag</p>
                </div>
                
                
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name:"Main",
    data(){
        return{
            posts: []
        }
    },
    created(){
        axios
        .get("/api/posts")
        .then((data_api)=>{
            this.posts = data_api.data
            console.log(this.posts);
        })
    }
}
</script>

<style lang="scss" scoped>
    
</style>