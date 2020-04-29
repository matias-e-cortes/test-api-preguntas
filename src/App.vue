<template>
    <div id="app">
        <!-- <img src="./assets/logo.png"> -->
        <!-- <router-view/> -->
        <app-test></app-test>


        <!-- <p>hola index</p> -->
    </div>
</template>

<script>
import Test from "./components/Test"


    export default {
      components: {
        "app-test" : Test,

      },
        name: "App",
    };
</script>

<style>

    body {
        background-color: lightblue;
    }


    #app {
        font-family: "Avenir", Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }


</style>
