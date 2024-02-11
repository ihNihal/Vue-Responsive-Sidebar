<template>
<aside :class = "`${is_expanded ? 'is_expanded' : ''}`">
  <div class="logo">
    <img src="../assets/logo.svg" alt="logo">
  </div>
  <div class="menu-toggle-wrap">
    <button class="menu-toggle" @click="ToggleMenu">
      <span class="material-icons">keyboard_double_arrow_right</span>
    </button>
  </div>
  <h3>Menu</h3>
  <div class="menu">
    <router-link class="button" to="/">
      <span class="material-icons">home</span>
      <span class="text">Home</span>
    </router-link>
    <router-link class="button" to="/about">
      <span class="material-icons">notes</span>
      <span class="text">About</span>
    </router-link>

  </div>
  <div class="flex"></div>
    <div class="menu">
    <router-link class="button" to="/settings">
      <span class="material-icons">settings</span>
      <span class="text">Settings</span>
    </router-link>
  </div>

</aside>
</template>

<script setup>

import {ref} from 'vue';
const is_expanded = ref(localStorage.getItem("is_expanded")==="true");
const ToggleMenu = () => {
  is_expanded.value = !is_expanded.value;
localStorage.setItem("is_expanded", is_expanded.value)
}

</script>

<style scoped>
aside{
  display: flex;
  flex-direction: column;
  background-color: darkslategrey;
  color:white;
  min-height: 100vh;
  width: calc(2rem + 32px);
  overflow:hidden;
  padding:1rem;
  transition:0.2s ease-out;

  .flex{
    flex:1 1 0;

  }

  .logo{
    margin-bottom: 2rem;
    img{
      width:2rem;
    }
  }
  h3, .button .text{
   opacity: 0;
    transition: 0.3s ease-out;
  }
  h3{
    color: grey;
    font-size:0.875rem;
    margin-bottom: 0.5rem;
    text-transform:uppercase;
  }
  .menu{
    margin: 0 -1rem;
    .button{
      display: flex;
      align-items: center;
      text-decoration: none;
      padding: 0.5rem 1rem;
      transition: 0.2s ease-out;
      .material-icons{
        font-size:2rem;
        color: white;
        transition: 0.2s ease-out;
      }
      .text{
        color: white;
        transition: 0.2s ease-out;

      }
      &:hover{
        background-color: #334155;
        .material-icons, .text{
          color:#4ade80;

        }
      }
      &.router-link-exact-active {
        background-color: var(--dark-alt);
        border-right: 5px solid var(--primary);

        .material-icons, .text {
          color: white;
        }
      }
    }
  }
  &.is_expanded{
    width:300px;
    .menu-toggle-wrap{
      top: -3rem;
      .menu-toggle{
        transform:rotate(-180deg)
      }
    }
    h3, .button .text{
      opacity: 1;

    }
    .button{
      .material-icons{
        margin-right:1rem;
      }
    }
      }
  .menu-toggle-wrap{
    display: flex;
    justify-content: flex-end;
    position:relative;
    margin-bottom: 1rem;
    top:0;
    transition: 0.2s ease-out;


    .menu-toggle{
      transition: 0.2s ease-out;
      .material-icons{
        font-size:2rem;
        color: white;
        background-color: darkslategrey;


      }
      &:hover{
        .material-icons{
          color:#4ade80;
          transform: translateX(0.5rem);
          transition: 0.2s ease-out;

        }
      }
    }
  }

  @media (max-width:768px){
    position:fixed;
    z-index: 99
  }
}


</style>