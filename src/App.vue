<template>
<section>
  <header>
    <h1>My Friends</h1>
  </header>
  <new-friend @add-contact="addContact"></new-friend>
  <ul>
    <!--in vue use cebap-case sintax; props se ne mogu menjati
    podaci odavde se mogu menjati samo ovde, ne u friendcontact komponenti (vezano za props)
    :is-favourite="true" - prop that need a js(non string values) value other then string use bind
    :key when we work with v-for
    :bind -  dinamicaly
    -->
   <friend-contact
      v-for="friend in friends"
      :key="friend.id"
      :id="friend.id"
      :name="friend.name"
      :phone-number="friend.phone"
      :email-address="friend.email"
      :is-favourite="friend.isFavourite"
      @toggle-favorite="toggleFavouriteStatus"
      @delete="deleteContact"
   >
   </friend-contact>
  </ul>
</section>
</template>

<script>
import FriendContact from './components/FriendContact.vue'
import NewFriend from './components/NewFriend.vue';
export default {
  name: 'App',
  components: {FriendContact, NewFriend},
  data(){
    return{
      friends:[
        {
        id:'maunel',
        name:'Manuel Lorenz',
        phone:'0123 456 789',
        email:'manuel@localhost.com',
        isFavourite:true
      },
      {
        id:'julie',
        name:'Julie Oliver',
        phone:'0123 4545 789',
        email:'julie@localhost.com',
        isFavourite:false
      }
      ],
    }
  },
  methods:{
    toggleFavouriteStatus(friendId){
      const identifierFriend = this.friends.find(friend => friend.id === friendId);
      identifierFriend.isFavourite = !identifierFriend.isFavourite;
    },
    addContact(name,phone,email){
      const newFriendContact = {
        id:new Date().toISOString(),
        name:name,
        phone:phone,
        email:email,
        isFavourite:false
      };
      this.friends.push(newFriendContact);
    },
    deleteContact(friendId){
      this.friends = this.friends.filter((friend) => friend.id !== friendId);
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>
