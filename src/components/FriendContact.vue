<template>
    <li>
        <h2>{{friend.name}}</h2>   
        <button @click="toggleDetails">Show details</button>
        <ul v-if="detailsAreVisible">
            <li>
                <strong>Phone:</strong> 
                {{friend.phone}}
            </li>
            <li>
                <strong>Email:</strong> 
                {{friend.email}}
            </li>
           </ul> 
    </li>
</template>

<script>
export default {
    data(){
        return{
            detailsAreVisible:false,
            firend:{
                id:'maunel',
                name:'Manuel Lorenz',
                phone:'0123 456 789',
                email:'maule@localhost.com'
            },
        };
    },
    methods:{
        toggleDetails(){
            this.detailsAreVisible = !this.detailsAreVisible;
        },
    }
}
</script>
