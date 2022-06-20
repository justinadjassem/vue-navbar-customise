<script lang="ts">
import Vue from 'vue';
import VueRouter from 'vue-router';
import { BootstrapVue, IconsPlugin } from 'bootstrap-vue'

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'


Vue.use(BootstrapVue)
Vue.use(IconsPlugin)
Vue.use(VueRouter);

export default /*#__PURE__*/Vue.extend({
  name: 'VueNavbarCustomise', // vue component name
    data() {
    return {
    //   prevRoute:"$router.go(-1)"
    }
  },
    props:{
        
        navShadow: {
            type:Boolean,
            default:true
            },
        bnavbarvariant: String,
        type: String,
        toggleable:{
            type: String,
            default: "lg"
        },
        username: {
            type: String,
            default: "username"
        },
        avatarUrl: {
            type: String,
            default: "https://i.pravatar.cc/200?img=51"
            },
        profileDisplayName: {
            type: String,
            default: ""
        }, 
        profileName: {
            type: String,
            default: "mon profil"
        },
        profilePath: {
            type: String,
            default: "/profile"
        },
         home: {
            type: String,
            default: "home"
        },
        homePath: {
            type: String,
            default: "/"
        },
        structureName: {
            type: String,
            default: "STRUCTURE NAME"
        },
        displayedBrand: {
            type: String,
            default: "BRAND"
        },
        brandClass: {
            type: String,
            default: "section-title"
        },
        structureNameClass: {
            type: String,
            default: "section-title"
        },
        currentRouteName: {
          type: String,
          default:"home"
        }   
    },

    methods: {
    menuClickEvent(routeName: string) {
      this.$router.push({ path: routeName });
    },
  },

  //   computed: {
  //   currentRouteName(): string {
  //     return this.$route.name!;
  //   },
  // },
    
})
</script>

<template>
     <div>
       <link href="https://fonts.googleapis.com/icon?family=Material+Icons"
      rel="stylesheet">
        <b-navbar :class="{'shadow': navShadow}" :toggleable="toggleable" :variant="bnavbarvariant" :type="type" >
                  
        <b-navbar-nav >
            <b-nav-item 
                 @click="$router.go(-1)"
              
                class="icon-border mx-2 p-0 "
            >
                <span class="material-icons mouse-pointer">home</span>
            </b-nav-item> 
            <div v-if="currentRouteName == home" class="icon-place"></div> 
            <b-nav-item v-if="currentRouteName != home"
                
                class="icon-border mx-2"  @click="menuClickEvent(homePath)"
            >
                <span class="material-icons mouse-pointer">arrow_back</span>
             </b-nav-item>
        </b-navbar-nav>
            
            <b-navbar-brand class="mx-2"
            >
            <span :class="brandClass"> <b> {{displayedBrand}} </b> </span>
            </b-navbar-brand>
            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav class="ml-auto  align-items-center justify-content-around">
                    <b-nav-text class="mouse-pointer px-5"
                    @click="menuClickEvent(home)"
                    >
                    <span :class="structureNameClass">{{ structureName }}</span>
                    </b-nav-text>
                    <b-nav-text>{{ username }}</b-nav-text>
                        <b-nav-item>
                            <b-avatar badge-variant="info" :src="avatarUrl"></b-avatar>  
                        </b-nav-item>                   
                    <b-nav-item >
                        <span id="tooltip_id" class="material-icons pt-16">power_settings_new</span>
                        <b-tooltip target="tooltip_id" placement="bottom" variant="dark" boundary-padding="50">
                            <b> Se déconnecter </b>
                        </b-tooltip>
                    </b-nav-item>
                </b-navbar-nav>
    </b-collapse>
        </b-navbar>
    </div>
</template>

<style lang="scss" >

.adjust{
    display: flex;
}
.mouse-pointer{
    cursor: pointer;
}
.icon-border{
    border: 1px solid rgba(192,192,192,0.3);
    border-radius: 5px;
    list-style: none;
}
.icon-border:hover {
border: 1px solid gray;
}
// .icon-place{
//     width: 116px;
//     height: 49.891px;
// }
/* // Extra small devices (portrait phones, less than 576px) */
@media (max-width: 575.98px) {
    
}

/* // Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) and (max-width: 767.98px) {
    
}

/* // Medium devices (tablets, 768px and up) */
@media (min-width: 768px) and (max-width: 991.98px) {     
    .icon-place{
    width: 24px;
    height: 30px;
    }
    
}

/* // Large devices (desktops, 992px and up) */
@media (min-width: 992px) and (max-width: 1199.98px) { 
     .icon-place{
        width: 24px;
        height: 30px;
        }
  
 }

/* // Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) {  
     .icon-place{
        width: 24px;
        height: 30px;
        }
  
}
</style>