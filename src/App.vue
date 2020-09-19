<template>
<div id="app" class="flex container h-full w-full ">
<!-- Font Awesome -->
  <link rel="stylesheet" 
        href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" 
        integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" 
        crossorigin="anonymous">
<!-- side nav bar -->
   <div class=" w-1/5 border-r border-lighter  px-8 py-2 flex flex-col justify-between">
        <div class="mb-10">
           <button class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue ml-12">
           <i class="fab fa-twitter "></i>
           </button>
            <div class=" ml-12">
             <button v-for="tab in tabs" :key="tab" @click="id = tab.id" :class="`focus:outline-none hover:text-blue flex items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto mb-3 ${ id === tab.id ? 'text-blue' : ''}`">
                <i :class="`${ tab.icon } text-2xl mr-4 text-left `"></i>
               <!-- <p class="text-lg font-semibold text-left hidden lg:block"> {{ tab.title }} </p> -->
              </button>
            </div>
            <button class="text-white bg-blue rounded-full font-semibold focus:outline-none w-full p-3 hover:bg-darkblue ml-3">
            Tweet
            </button>
        </div>
        <div class="w-full">
        <button class="flex items-center hover:bg-lightest rounded-full w-full  ">
        <img src="../public/profile.jpg" class="w-12 h-12 rounded-full m-0 "/>
            
               <p class="text-xs font-bold ml-0 mr-5  ">Mubashir<br>45191<br><span class="text-xs ml-0 mr-3 font-normal">@Mub45191</span></p>
               
               
          
            <i class="fas fa-angle-down ml-auto text-lg"></i>
        </button>
        </div>
   </div>
 </div>
</template>

<script>
export default {
    name: 'App',
    components: {
    },
    data(){
       return{
         tabs: [
        {icon: 'fas fa-home', title: 'Home', id:'home'},
        {icon: 'fas fa-hashtag', title: 'Explore', id: 'explore'},
        {icon: 'far fa-bell', title: 'Notifications', id: 'notifications'},
        {icon: 'far fa-envelope', title: 'Messages', id: 'messages'},
        {icon: 'far fa-bookmark', title: 'Bookmarks', id: 'bookmarks'},
        {icon: 'fas fa-clipboard-list', title: 'Lists', id: 'lists'},
        {icon: 'far fa-user', title: 'Profile', id: 'profile'},
        {icon: 'fas fa-ellipsis-h', title: 'More', id: 'more'}
      ],
      id: 'home'
       }
    }
}
</script>

<style>
@import "../src/css/styles.css"


</style>
