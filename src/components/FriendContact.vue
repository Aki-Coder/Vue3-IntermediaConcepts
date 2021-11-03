<template>
    <li>
        <h2>{{name}}</h2>   
        <button @click="toggleDetails">{{detailsAreVisible ? 'Hide' : 'Show'}} Deatils</button>
        <ul v-if="detailsAreVisible">
            <li>
                <strong>Phone:</strong> 
                {{phoneNumber}}
            </li>
            <li>
                <strong>Email:</strong> 
                {{emailAddress}}
            </li>
           </ul> 
    </li>
</template>

<script>
export default {
    props:[
        'name',
        'phoneNumber',
        'emailAddress',
    ],
    data(){
        return{
            detailsAreVisible:false,
            friend:{
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
