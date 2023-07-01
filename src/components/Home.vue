<template>
    <div>
    <Header/>
    <h1> Hello User, welcome to Our Home Page</h1>
    </div>
</template>


<script>
import Header from './Header.vue'

export default {
    name:'Home',
    components: 
    {
    Header
    },
    // mounted() {

    //     let user = localStorage.getItem('user-info');
    //     if (!user) 
    //     {
    //         this.$router.push({ name: 'SignUp' })

    //     }
    // }
    //removed this coz i want my customer to peruse the product 
    //instead of forcing them to sign up 1st which can be a turn off
        
        
    
}
</script>
