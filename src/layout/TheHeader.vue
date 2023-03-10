<template>
  <header class="header_container">
    <div class="header">
      <div class="header_main">
        <base-logo class="header_logo"></base-logo>
        <nav class="header_nav" :class="{ open: isOpen }">
          <ul class="header_nav_list">
            <li v-for="link in links" :key="link.id"  class="header_nav_list_link" @click="switchNavList">
              <a :href="`#${link.id}`" class="header_nav_list_item">
                {{ link.name }}
              </a>
            </li>
          </ul>
        </nav>
      </div>
      <div class="header_additional">
        <transition>
          <input v-if="searchIsVisible"
          type="text"
          class="header_input"
          placeholder="Let's start"
        />
        </transition>
        <button class="header_search">
          <img
          :src="Search"
          alt="search"
          v-on:click="switchSearch"
        />
        </button>
        <base-transparent-button
          class="header_button"
        ></base-transparent-button>
        <button  class="header_download" >
          <img :src="Download" alt="download"/>
        </button>
        <button class="header_burger" v-on:click="switchNav">
          <img v-if="!isOpen" :src="Burger" alt="burger_button" class="header_burger_img" />
          <img v-if="isOpen" :src="Close" alt="close_button" class="header_close_img" />
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
import { reactive, ref } from "vue";
import Search from "@/assets/icons/search.svg";
import Download from "@/assets/icons/arrow.svg";
import Burger from "@/assets/icons/burger.svg";
import Close from "@/assets/icons/close.svg";
import { switchLock } from "../helpers";
const links = reactive([
  { name: "Discover", id: "primary" },
  { name: "Marketplace", id: "gallery" },
  { name: "More", id: "creators" },
]);
const isOpen = ref(false);
const searchIsVisible = ref(false);

function switchNav() {
  isOpen.value = !isOpen.value;
  switchLock(isOpen.value);
}

function switchNavList() {
  isOpen.value = false;
  switchLock(isOpen.value);
}

function switchSearch() {
  searchIsVisible.value = !searchIsVisible.value;
}
</script>

<style scoped lang="scss">
$bgc: #131313;

.header_container {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 7;
}



.header {
  background-color: $bgc;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 50px 20px;

  @media (min-width: 1024px) {
    padding: 50px 45px;
  }

  @media (min-width: 1440px) {
    padding: 63px 88px 43px 66px;
  }

  &_main {
    display: flex;
    align-items: center;
    gap: 25px;
  }

  &_additional {
    display: flex;
    gap: 28px;
    justify-content: center;
    align-items: center;

    @media (min-width: 768px) {
      gap: 20px;
    }
  }

  &_logo {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0;
  }

  @media (min-width: 768px) {
    gap: 40px;
  }

  &_nav {
    top: 0;
    left: 0;
    width: 100%;
    background-color: #131313;
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: absolute;
    transform: translate(-100%, 0);
    transition: transform 0.2s ease-out;
    cursor: pointer;

    @media (min-width: 768px) {
      transform: none;
      position: relative;
    }

    &.open {
      transform: translate(0, 0);
      flex-direction: column;
      align-items: center;
      left:0;
      top: 0;
      height: 100vh;
      border: 0.3px solid transparent;
      
    }

    &_list {
      display: flex;
      flex-direction: column;
      gap: 50px;
      list-style-type: none;
      font-size: 50px;
      margin-block-start: 120px;
      margin-block-end: 0;
      padding-inline-start: 0;
      width: 100%;

      &_link {
        display: flex;
        height: 88px;
        width: 100%;
        justify-content: center;
        align-items: center;
        text-align: center;
        border-top: 0.5px solid rgb(255, 255, 255);
        border-bottom: 0.5px solid rgb(255, 255, 255);


        @media (min-width: 768px) {
        text-align: left;
        border-top: 0.5px solid transparent;
        border-bottom: 0.5px solid transparent;
      }

      }


      @media (min-width: 768px) {
        flex-direction: row;
        gap: 30px;
        margin-block-start: 0;
        margin: 0;
        line-height: 10px;
        width: auto;
      }

      &_item {
        height: 88px;
        width: 100%;
        display: flex;
        align-items:center;
        justify-content: center;    
        font-family: "Arial";
        font-weight: 400;
        line-height: 25px;
        font-size: 22px;
        color: #ffffff;
        text-decoration: none;
        cursor: pointer;
        transition: all 0.3s ease-out;

        

        &:hover {
          color: #5ba300;
        }
      }
    }
  }
  .header_burger {
    z-index: 10;
    line-height: 0;
    box-sizing: border-box;
    cursor: pointer;

    &_img,
    .header_close_img {
      background-color: transparent;
      display: flex;
      justify-content: center;
      align-items: center;
      width: 30px;
      height: 30px;
    }
  }

  .header_input {
    border: 1px solid rgb(62, 69, 60);
    border-radius: 24px;
    background-color: transparent;
    padding: 12px 13px;
    font-weight: 400;
    font-size: 14px;
    line-height: 15px;
    color: rgba(255, 255, 255, 0.6);

    &:focus {
      border: 1px solid #5ba300;
    }

    &:focus::placeholder {
      opacity: 0;
    }
  }

  .v-enter-from {
    opacity: 0;
    transform: translateY(-30px);
  }

  .v-enter-active {
    transition: all 0.4s ease-out;
  }

  .v-enter-to {
    opacity: 1;
    transform: translateY(0);
  }

  .v-leave-from {
    opacity: 1;
    transform: translateY(0);
  }

  .v-leave-active {
    transition: all 0.4s ease-out;
  }

  .v-leave-to {
    opacity: 0;
    transform: translateY(-30px);
  }

  &_search {
    cursor: pointer;
    display: none;
    background-color: transparent;
    border: none;
    transition: all 0.3s ease-out;

    &:hover {
      transform: translateY(-5px);
    }

    @media (min-width: 1200px) {
      display: block;
    }
  }

  &_download {
    background-color: #5ba300;
    padding: 14px;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    border: none;
    transition: all 0.3s ease-out;

    &:hover {
      background-color: #5ba300;
      box-shadow: 0 0 5px #5ba300;
      transform: translateY(-5px);
    }

    &:active {
      background-color: #84c436;
    }
  }

  &_button {
    display: none;

    @media (min-width: 800px) {
      display: block;
      cursor: pointer;
    }
  }

  &_burger {
    background-color: $bgc;
    border: none;
    padding: 0;
    margin: 0;

    @media (min-width: 768px) {
      display: none;
    }
  }

}
</style>
