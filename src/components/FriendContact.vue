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
    //data from parent component
    // props:[
    //     'name',
    //     'phoneNumber',
    //     'emailAddress',
    //     'isFavourite',
    // ],
    props:{
        name:{
            type:String,
            reqiured:true
        },
        phoneNumber:{
            type:String,
            reqiured:true
        },
        emailAddress:{
            type:String,
            reqiured:true
        },
        isFavourite:{
            type:String,
            reqiured:false,
            default:'0',
            validator(value){
                return value === '1' || value === '0';
            }
        }
    },
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
