<template>
    <div class="Hook">
        <h1>Posts</h1><hr/>
        <input type="text" placeholder="Search" v-model="SearchTerm">
        <div v-for="post in filterSearch" :key="post.id">
            <h2>{{ post.title }}</h2>
            <p>{{ post.body | snippet }}</p>

        </div>

    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Hook',
    data(){
        return{
            posts:[],
            SearchTerm: ''
            
        }
        
    },
    computed: {
            filterSearch(){
                return this.posts.filter(post=>{
                    return post.title.match(this.SearchTerm)
                })
            }
        },
    methods:{

    },
    mounted(){
        axios.get('https://jsonplaceholder.typicode.com/posts')
        .then(res=>{
            this.posts = res.data
        })
        .catch(error=>{
            console.log(error)
        })

    }
    
}
</script>

<style scoped>
nav{
    text-align: center
}
nav ul{
    padding: 0
}
nav li{
    display: inline-block;
    list-style-type: none;
    margin: 0;
    padding: 8px;
}

</style>

