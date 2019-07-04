<template>
  <div id="app">
    <h2>{{ title }}</h2>
    <Nav></Nav>
      <AllFriends :friends="friends" @delete="deleteFriend"></AllFriends>
        <OnlineFriends :friends="friends"></OnlineFriends>
          <Hook></Hook>
        
      
    
  </div>
</template>

<script>
import Nav from './components/Nav'
import AllFriends from './components/AllFriends'
import OnlineFriends from './components/OnlineFriends'
import Hook from './components/Hook'

export default {
  name: 'app',
  data(){
    return{
      title: 'Allah valo ekta bebostha korben as soon as',
      friends:[
                {name:'A', online:true},
                {name:'B', online:true},
                {name:'C', online:false},
                {name:'D', online:true},
                {name:'E', online:true}
            ]
    }
  },
  components:{
    Nav,
    OnlineFriends,
    AllFriends,
    Hook
  },
  methods:{
    deleteFriend(payload){
      this.friends = this.friends.filter(friend=>{
        return friend.name !== payload.name
      })

    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
