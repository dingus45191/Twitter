<template>
<div id="app" class="flex container h-full w-full ">
<!-- Font Awesome -->
  <link rel="stylesheet" 
        href="https://use.fontawesome.com/releases/v5.2.0/css/all.css" 
        integrity="sha384-hWVjflwFxL6sNzntih27bfxkr27PmbbK/iSvJ+a4+0owXq79v+lsFkW54bOGbiDQ" 
        crossorigin="anonymous">
<!-- side nav bar -->
   <div class=" lg:w-1/5 border-r border-lighter  sm:px-5 px-8 py-2 flex flex-col justify-between  ">
        <div class="mb-10 ">
           <button class="h-12 w-12 hover:bg-lightblue text-3xl rounded-full text-blue ml-9 mb-2">
           <i class="fab fa-twitter "></i>
           </button>
            <div class=" ml-8 ">
             <button v-for="tab in tabs" :key="tab" @click="id = tab.id" :class="`focus:outline-none hover:text-blue flex items-center py-2 px-4 hover:bg-lightblue rounded-full mr-auto mb-3 ${ id === tab.id ? 'text-blue' : ''}`">
                <i :class="`${ tab.icon } text-2xl mr-4 text-left `"></i>
                <p class="text-lg font-semibold text-left hidden lg:block"> {{ tab.title }} </p> 
              </button>
            </div>
            <button class="text-white bg-blue rounded-full font-semibold focus:outline-none w-12 h-12 lg:h-auto lg:w-full p-3 hover:bg-darkblue ml-3 mb-20">
            <div class="sm:ml-6">
            <p class="hidden lg:block ">Tweet</p>
            <div class="md:hidden">
             <i  class="fas fa-plus hidden sm:block md:block"></i>
            </div>
            </div>
           
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
   <!--Tweets-->
    <div class="w-1/2 h-full overflow-y-scroll">
    <div class="px-5 py-3 border-b border-lighter flex items-center justify-between">
       <h1 class="text-xl font-bold">Home</h1>
       <i class="far fa-star text-xl text-blue"></i>
    </div>
    <div class="px-5 py-3 border-b-8 border-lighter flex">
      <div >
        <img src="profile.jpg" class="w-12 h-12 rounded-full"/>
      </div>
      <form class="w-full px-4 relative">
        <textarea placeholder="What's up?" class="w-full focus:outline-none"></textarea>
        <div class="flex items-center">
            <i class="text-lg text-blue mr-4 far fa-image"></i>
            <i class="text-lg text-blue mr-4 fas fa-film"></i>
            <i class="text-lg text-blue mr-4 far fa-chart-bar"></i>
            <i class="text-lg text-blue mr-4 far fa-smile"></i>
        </div>
        <button class="h-10 px-4 text-white font-semibold bg-blue"
      </form>
    </div>
   </div> 

   <!--Trending-->
   <div class="md:block hidden w-1/3 h-full border-l border-lighter py-2 px-6  relative">
     <input class=" pl-12 rounded-full w-full p-2 bg-lighter text-sm" placeholder="Search Twitter" />
     <i class="fas fa-search absolute top-4 left-0 ml-12 mt-1 text-sm text-light"></i>
         <div class=" w-full rounded-lg bg-lightest">
             <div class="flex items-center justify-between p-3 mt-5">
               <p class="text-lg font-bold ">Trends for You</p>
                <i class="fas fa-cog text-lg text-blue"></i>
             </div>
             <button v-for="trend in trending" :key="trend" class="w-full flex justify-between hover:bg-lighter p-3 border-t border-lighter">
                 <div class="">
                    <p class="text-sm text-left leading-tight"> {{trend.top}} </p>
                    <p class="font-bold text-left leading-tight"> {{trend.title}} </p>
                    <p class="text-left leading-tight text-dark"> {{trend.bottom}} </p>
                    
                 </div>
                 <i class="fas fa-angle-down text-lg text-dark"></i>
             </button>
             <button class="p-3 w-full hover:bg-lighter text-left text-blue border-t border-lighter">
             Show more
             </button>
         </div>
         
         <!-- Following section -->
          <div class=" w-full rounded-lg bg-lightest">
             <div class=" p-3 mt-5">
               <p class="text-lg font-bold ">Who to Follow</p>
               
             </div>
             <button  v-for="ally in allies" :key="ally" class="w-full flex hover:bg-lighter p-3 border-t border-lighter">
                <img :src="`${ally.src}`" class="w-12 h-12 rounded-full m-0 "/>
                   
                      <p class="text-xs font-bold ml-0 mr-5 hidden lg:block ">{{ally.name}}<br><span class="text-xs ml-0 mr-3 font-normal">{{ally.handle}}</span></p>
                      
                      
                 
                  <button class="ml-auto text-sm text-blue py-1 px-4 rounded-full border-2 border-blue">Follow</button>
             </button>
             <button class="p-3 w-full hover:bg-lighter text-left text-blue border-t border-lighter">
             Show more
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
      id: 'home', 
      dropdown: false,
      trending: [
        
        {top: 'Economy', title: 'Covid crisis', bottom: 'Recession?'},
        {top: 'Investing', title: 'Gold', bottom: 'Death of dollar?'},
        {top: 'Trending in US', title: 'Elections', bottom: 'Trump vs Biden'},
        {top: 'Business', title: 'Tech Startups', bottom: 'Hot Startups'},
        {top: 'Trending', title: 'Vue.js v3', bottom: '25.4k tweets'},
      ],
       allies: [
        {src: 'elon.jpg', name: 'Elon Musk', handle: '@elMusk'},
        {src: 'obama.jpg', name: 'Barrack Obama', handle: '@bObama'},
        {src: 'trump.jpg', name: 'Donald Trump', handle: '@realDon'}
      ]
       }
    }
}
</script>

<style>
@import "../src/css/styles.css"


</style>
