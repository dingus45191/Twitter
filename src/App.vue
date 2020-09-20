<template>
<div id="app" class="flex container h-full w-full ">
<!-- Font Awesome -->
  <link rel="stylesheet" 
        href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" 
        integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" 
        crossorigin="anonymous">
<!-- side nav bar -->
   <div class=" w-1/5 border-r border-lighter sm:md:px-2 lg: px-8 py-2 flex flex-col justify-between">
        <div class="mb-10">
           <button class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue ml-9 mb-2">
           <i class="fab fa-twitter "></i>
           </button>
            <div class=" ml-8">
             <button v-for="tab in tabs" :key="tab" @click="id = tab.id" :class="`focus:outline-none hover:text-blue flex items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto mb-3 ${ id === tab.id ? 'text-blue' : ''}`">
                <i :class="`${ tab.icon } text-2xl mr-4 text-left `"></i>
                <p class="text-lg font-semibold text-left hidden lg:block"> {{ tab.title }} </p> 
              </button>
            </div>
            <button class="text-white bg-blue rounded-full font-semibold focus:outline-none w-12 h-12 lg:h-auto lg:w-full p-3 hover:bg-darkblue ml-3 mb-20">
            <p class="hidden lg:block">Tweet</p>
            <i class="fas fa-plus lg:hidden"></i>
            </button>
        </div>
        <div class="lg:w-full relative">
              <button @click="dropdown = true" class="flex items-center hover:bg-lightblue rounded-full w-full focus:outline-none  ">
              <img src="../public/profile.jpg" class="w-10 h-10 rounded-full m-0 "/>
                  
                     <p class="text-xs font-bold ml-0 mr-5 hidden lg:block ">Mubashir45191<br><span class="text-xs ml-0 mr-3 font-normal">@Mub45191</span></p>
                     
                     
                
                  <i class="fas fa-angle-down ml-auto text-lg hidden lg:block"></i>
              </button>
             <div v-if="dropdown===true" class="absolute bottom-0 left-0 w-64 rounded-lg shadow-md border-lightest bg-white mb-15   ">
               <button @click="dropdown=false" class="flex items-center hover:bg-lightest w-full focus:outline-none  ">
                <img src="../public/profile.jpg" class="w-10 h-10 rounded-full m-0 "/>
                  
                     <p class="text-xs font-bold ml-0  ">Mubashir45191<br><span class="text-xs ml-0 mr-0 font-normal">@Mub45191</span></p>
                       
                       
                  
                    <i class="fas fa-check ml-auto text-blue"></i>
                 </button>
                 <button @click="dropdown=false" class="w-full text-left hover:bg-lightest border-t border-gray-100 p-3 text-sm focus:outline-none ">
                Add an existing account.
                 </button>
                 <button @click="dropdown=false" class="w-full text-left hover:bg-lightest border-t border-gray-100 p-3 text-sm focus:outline-none ">
                Log out @Mub45191
                 </button>
             </div>
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
      id: 'home', 
      dropdown: false
       }
    }
}
</script>

<style>
@import "../src/css/styles.css"


</style>
