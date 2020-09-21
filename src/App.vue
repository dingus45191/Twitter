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
      <form  v-on:submit.prevent="newTweet" class="w-full px-4 relative">
        <textarea v-model="tweet.content" placeholder="What's up?" class="pb-3 mt-3 w-full focus:outline-none"></textarea>
        <div class="flex items-center">
            <i class="text-lg text-blue mr-4 far fa-image"></i>
            <i class="text-lg text-blue mr-4 fas fa-film"></i>
            <i class="text-lg text-blue mr-4 far fa-chart-bar"></i>
            <i class="text-lg text-blue mr-4 far fa-smile"></i>
        </div>
        <button  type="submit" class="h-10 px-4 text-white font-semibold bg-blue hover:bg-darkblue focus:outline-none rounded-full absolute bottom-0 right-0">
        Tweet
        </button>
      </form>
    </div>
    <div v-for="follow in following" :key="follow" class="w-full p-4 border-b hover:bg-lighter flex ">
     <div class="flex-none mr-4">
       <img :src="`${follow.src}`" :key="follow.src" class="h-12 w-12 rounded-full flex-none"  alt="image">
     </div>
      <div class="w-full">
          <div class="flex items-center w-full">
            <p class="font-semibold">{{follow.name}}</p>
            <p class="text-sm text-dark ml-2">{{follow.handle}}</p>
            <p class="text-sm text-dark ml-2">{{follow.time}}</p>
            <i class="fas fa-angle-down text-dark ml-auto"></i>
          </div>
        <p class="py-2">{{follow.tweet}}</p>
        <div class="flex items-center justify-between w-full">
            <div class="flex items-center text-sm text-dark">
              <i class="far fa-comment mr-3"></i>
              <p>{{follow.comments}} </p>
            </div>
            <div class="flex items-center text-sm text-dark">
              <i class="fas fa-retweet mr-3"></i>
              <p>{{follow.retweets}}</p>
            </div>
              <div class="flex items-center text-sm text-dark">
                <i class="fas fa-heart"></i>
                <p>{{follow.like}}</p>
              </div>
                <div class="flex items-center text-sm text-dark">
                  <i class="fas fa-share-square mr-3"></i>

                </div>
        </div>
      </div>
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
        {top: 'Technology', title: 'Vue.js ', bottom: `Will Vue kill React and Angular?It's already winning`},
        {top: 'Business', title: 'Tech Startups', bottom: 'Hot Startups'},
        {top: 'Trending', title: 'Elections in US. Trump vs Biden', bottom: '100k Tweets'}

      ],
       allies: [
        {src: 'elon.jpg', name: 'Elon Musk', handle: '@elMusk'},
        {src: 'obama.jpg', name: 'Barrack Obama', handle: '@bObama'},
        {src: 'trump.jpg', name: 'Donald Trump', handle: '@realDon'}
      ],
         following: [
           {src: 'obama.jpg', name: 'Barrack Obama', handle: '@bObama', time: '20 min', tweet: `@elMusk you should send @realDon to Mars forever. The guy's destroying America.`, comments: '30,000', retweets: '55000', like: '8,000,003'},
           {src: 'elon.jpg', name: 'Elon Musk', handle: '@elMusk', time: '55 min', tweet: `Well I can send him for a tour but forever??I'd better not use SpaceX for these stuff.`, comments: '80,030', retweets: '50', like: '20,003'},
           {src: 'profile.jpg', name: 'Mubashir45191', handle: '@Mub45191', time: '1.4 hr', tweet: `@elMusk and @realDon which one is the best laptop, Macbook Pro or Dell XPS`, comments: '50,000', retweets: '1,000,002', like: '5,000,003'},
           {src: 'trump.jpg', name: 'Donald Trump', handle: '@realDon', time: '1.5 hr', tweet: `Well I'm a legend I will settle on Mars if @elMusk succeeds in colonizing it. Stupid of @bObama. @Mub45191 I'd go with mac.`, comments: '100,500', retweets: '1,000,032', like: '5,000,103'},
           {src: 'elon.jpg', name: 'Elon Musk', handle: '@elMusk', time: '2hr', tweet: `@Mub45191 I'd say choose Macbook. It's awesome.You can do everything with a mac.`, comments: '20,030', retweets: '5000', like: '50,200'}
         ],
         tweets:[
           {content:'Ok cool, I should get a Mac.'}
         ],
         tweet: {content:''}
       }
    },
  methods:{
      newTweet(){
        let newTweetn = {
          content: this.tweet.content
        };
        this.tweets.push(newTweetn);
      }
  }
}
</script>

<style>
@import "../src/css/styles.css"


</style>
