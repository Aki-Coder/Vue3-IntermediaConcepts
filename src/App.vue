<template>
<section>
  <h2>My Friends</h2>
  <ul>
   <friend-contact></friend-contact>
   <friend-contact></friend-contact>
  </ul>
</section>
</template>

<script>
import FriendContact from './components/FriendContact.vue'
export default {
  name: 'App',
  components: {FriendContact},
  data(){
    return{
      friends:[
        {
        id:'maunel',
        name:'Manuel Lorenz',
        phone:'0123 456 789',
        email:'maule@localhost.com'
      },
      {
        id:'julie',
        name:'Julie Oliver',
        phone:'0123 4545 789',
        email:'julie@localhost.com'
      }
      ],
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
