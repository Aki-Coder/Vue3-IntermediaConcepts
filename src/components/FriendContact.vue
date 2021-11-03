<template>
    <li>
        <h2>{{name}} {{friendIsFavourite ? '(Favourite)' : ''}}</h2>   
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
            type:Boolean,
            reqiured:false,
            default:false,
            // validator(value){
            //     return value === '1' || value === '0';
            // }
        }
    },
    data(){
        return{
            detailsAreVisible:false,
            friendIsFavourite: this.isFavourite,
        };
    },
    methods:{
        toggleDetails(){
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        toggleFavourite(){
            this.friendIsFavourite = !this.friendIsFavourite;
        }
    }
}
</script>
