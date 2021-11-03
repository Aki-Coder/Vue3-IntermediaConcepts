<template>
    <li>
        <h2>{{name}} {{friendIsFavourite === '1' ? '(Favourite)' : ''}}</h2>   
        <button @click="toggleFavourite"> Toggle Favourite</button>
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
        'isFavourite',
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
            friendIsFavourite: this.isFavourite,
        };
    },
    methods:{
        toggleDetails(){
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavourite(){
            if(this.friendIsFavourite === '1'){
                this.friendIsFavourite = '0';
            }else{
                this.friendIsFavourite = '1';
            }
        }
    }
}
</script>
