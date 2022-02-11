<template>
    <li>
        <h2>{{name}} {{isFavourite ? '(Favourite)' : ''}}</h2>   
        <button @click="toggleFavourite"> Toggle Favourite</button>
        <button @click="toggleDetails">{{detailsAreVisible ? 'Hide' : 'Show'}} Deatils</button>
        <ul v-if="detailsAreVisible">
            <li>
                <strong>Phone:</strong> 
                <!--access to props-->
                {{phoneNumber}}
            </li>
            <li>
                <strong>Email:</strong> 
                {{emailAddress}}
            </li>
           </ul> 
           <button @click="$emit('delete', id)">Delete</button>
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
    //in js use pacalCase sintax-->
    props:{
        id:{
            type:String,
            reqiured:true
        },
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
            //when required is false you can add default
            default:false,
            // validator(value){
            //     return value === '1' || value === '0';
            // }
        }
    },
    //you will define which custom events your component will eventually at some point emit.
    emits:['toggle-favorite','delete'],
    //second way of definig & validating custom events
    // emits:{
    //     'toggle-favorite':function(id){
    //         if(id){
    //             return true;
    //         }else{
    //             console.warn('Id is missing');
    //             return false;
    //         }
    //     }
    // },

    data(){
        return{
            detailsAreVisible:false,
            //dodamo novi property(vezano za props izmene)
            //friendIsFavourite: this.isFavourite,
        };
    },
    methods:{
        toggleDetails(){
            this.detailsAreVisible = !this.detailsAreVisible;
        },
        // toggleFavourite(){
        //     this.friendIsFavourite = !this.friendIsFavourite;
        // },
         toggleFavourite(){
            this.$emit('toggle-favorite', this.id);
        },
        // deleteFriend(){
        //     this.$emit('delete');
        // }
    }
}
</script>
