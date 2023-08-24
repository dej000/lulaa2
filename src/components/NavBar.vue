
<script>
import Logo from './Logo.vue';


    export default {
      components:{
     Logo,
  
  },
  data(){
            return{
                scrolledNav:null,
                mobile:null,
                mobileNav:null,
                windowWidth:null,
            }
        },
        created(){
            window.addEventListener('resize',this.checkScreen)
            this.checkScreen()
        },

        mounted(){
            window.addEventListener('scroll',this.updateScroll)
        },
        methods: {
            toggleMobileNav(){
                this.mobileNav =!this.mobileNav;
                
            },

            updateScroll() {
                const scrollPosition = window.scrollY;
                if(scrollPosition > 460){
                    this.scrolledNav = true;
                    return
                }
                this.scrolledNav = false
            },

            checkScreen(){
                this.windowWidth =window.innerWidth;
                if(this.windowWidth <= 1000){
                    this.mobile = true
                    return
                }
                this.mobile = false;
                this.mobileNav = false;
                return;
            },
            scrollToTop(){
              window.scrollTo(0, 0);
            }
        },
    }
</script>
<template>
 
    <header class="header container gap-5 pl-5 pr-5 " :class="{'scrolled-nav':scrolledNav}"> 
      <a class="navbar-brand  " href="/"><Logo src="" /></a>
    <nav class="navbar d-flex align-items-center   ">
      <div v-show="!mobile" >
          <div class="navbar1 d-flex   ">
            <div>
              <ul class="navigation d-flex gap-4">
                <router-link   class="nav-link  "  to="">Home</router-link>
                <router-link  class="nav-link "  to="">Events</router-link>
                <router-link    class="nav-link "  to="">About us</router-link>
                <router-link     class="nav-link "  to="">Blog</router-link>
                <router-link    class="nav-link "  to="">Contact</router-link>
          
            </ul> 
            </div>

          </div>
        
        </div>
        <div  v-show="!mobile">
          <div class="d-flex align-items-center gap-5">
           
            <router-link @click="scrollToTop"    class="nav-link "  to="">FAQ</router-link>
            <router-link @click="scrollToTop"    class="nav-link "  to="">Pricing</router-link>
            <router-link @click="scrollToTop"     class="btn sign"  to="">Login</router-link>
            
         </div>
        </div>
       
       </nav> 
      
      <div class="icon">
        <svg @click="toggleMobileNav" v-show="mobile" :class="{'icon-active':mobileNav}" width="39" height="26" viewBox="0 0 39 26" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M2 2H8.5625M37 2H17.3125M37 24H30.4375M2 24H21.6875M2 13H37" stroke="white" stroke-width="4" stroke-linecap="round"/>
          </svg>
          
      
      </div>

     
       <ul v-show="mobileNav" class="dropdown-nav">
        <router-link  @click="toggleMobileNav()"  class="nav-link "  to="">Home</router-link>
        <router-link  @click="toggleMobileNav();"  class="nav-link"  to="">Events</router-link>
           <router-link  @click="toggleMobileNav()"  class="nav-link"  to="">About us</router-link>
           <router-link  @click="toggleMobileNav() "  class="nav-link"  to="">Blog</router-link>
           <router-link  @click="toggleMobileNav() "  class="nav-link"  to="">Contact</router-link>
            
           <div class="d-flex flex-column ">
            <router-link @click="toggleMobileNav()"    class="btn sign"  to="">Login</router-link>
             <!-- <a href=""><button type="button" class="sign ">Login</button> </a>  -->
             
         </div>
       
       </ul>   
      

   </header>

</template>
<style scoped>

 .log{
   
    color: white;
    width: 100px;
    font-size: 16px;
    font-weight: 500;
    background-color:#43438A;
 }

 .sign{
    width: 100px;
    color: #ffffff;
    font-size: 16px;
    font-weight: 500;
    border: 2px solid #ffffff ;
    background: none;

 }
 .nav-link{
  padding-right:20px ;
  color: #ffffff !important;
font-size: 16px !important;
 }
 
 .active {
  background-color: #383850 !important;
 }

 

 .header{
  display: flex;
  align-items: center;
  transition: .5s ease all;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  right: 0;
  background:rgb(255, 249, 249,-9.1);
  z-index: 9999;

  
}
nav.navbar{
  display: flex;
  width: 100%;
  flex-wrap: nowrap;

}


nav.navbar a{
color: #fefefe;
font-size: 16px;

}

@font-face {
  font-family: 'Beausite Fit';
  src: url('@fonts/'),
       ;
  
}

.custom-font {
  font-family: 'Beausite Fit', sans-serif;
}







.icon{
  color:#f7f7f7;
  cursor: pointer;
}

.icon i{
  transition: 0.8s ease all;
}

.icon-active{
  transform: rotate(180deg);
}

.dropdown-nav{
  display: flex;
  flex-direction: column;
  position: fixed;
  width: 100%;
  height: 100vh;
  background: rgb(0, 0, 0);
  top: 46px;
  left: 0;
  gap: 20px;
  transition: height .2s ease-in-out;
  padding: 20px;
  font-size: 40px; 
  color: #ffffff;
  z-index: 100;
} 

 .nav-links{
  
  font-size: 40px; 
  color: #ffffff;
  
} 



.dropdown-nav li{
   margin-left: 0;
   list-style: none;
   
}

.dropdown-nav a{
  color: #97979c;
  text-decoration: none;
  padding: 5px;
}

.dropdown-nav a:hover{
  color: #143F6B;
  box-shadow: inset 100px 0 0 0 #c4c9ca;

}





.navigation{
  display: flex;
  align-items: center;
 
}

.navigation {
  list-style: none;
  padding: 10px;
  display: flex;
  white-space: nowrap;
  
}

ul.navigation{
  margin-bottom: 0;
  padding-left: 0;
}


nav.navbar a{
  box-shadow: inset 0 0 0 0 #4e5051;
  color: #ffffff; 
  padding: 4px;
  font-size: 20px;
  transition: color .3s ease-in-out, box-shadow .3s ease-in-out ;
  text-decoration: none;
}





@media (max-width :1124px){
  .header .nav-links{
      display: none ;
   }
   .header{
    padding: 10px;
   }
  
   .header .nav-links.active{
      position: fixed;
      height: 100vh;
      width: 100%;
      top: 0;
      left: 0;
      display: flex;
      flex-direction: column ;
      justify-content: center;
      align-items: center;
      background: white;
      
   }
  

  
  
   header nav.navbar a{
      box-shadow: inset 0 0 0 0 #54b3d6;
      color: #fcfcfc;
      font-weight:bold;
      padding: 4px;
      font-size: 14px;
      transition: color .3s ease-in-out, box-shadow .3s ease-in-out ;
      
  }
  
  
}

</style>