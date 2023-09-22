***RUN COMMANDS IN ORDER***

**Requites Node.JS and Composer**

***ONLY RUN THIS COMMAND IS YOU HAVEN'T RUN IT BEFORE***
```
composer global require laravel/installer
```

## Creating App
```
laravel new [APP-NAME]
none
0
yes
mysql

cd [APP-NAME]
```

## Adding Vue
```
composer require laravel/ui

php artisan ui vue

npm install
```

## Adding Vue Things
```
npm install vue-router

npm install -D tailwindcss postcss autoprefixer

npx tailwindcss init -p
```

## Tailwind config
==Place this code in /tailwind.config.js==
```
/** @type {import('tailwindcss').Config} */

module.exports = {

  content: [

    "./resources/**/*.blade.php",

    "./resources/**/*.js",

    "./resources/**/*.vue",

  ],

  theme: {

    extend: {},

  },

  plugins: [],

}
```

## CSS setup
==Place below code in /resources/css/app.css==
```
@tailwind base;

@tailwind components;

@tailwind utilities;

  

*,

*::before,

*::after {

    box-sizing: border-box;

}

  

* {

    margin: 0;

    padding: 0;

    font: inherit;

}

  

body {

}

  

img,

picture,

svg,

video {

    display: block;

    max-width: 100%;

}

  

/* Chrome, Safari, Edge, Opera */

input::-webkit-outer-spin-button,

input::-webkit-inner-spin-button {

    -webkit-appearance: none;

    margin: 0;

}

  

/* Firefox */

input[type="number"] {

    -moz-appearance: textfield;

}

  

input:focus,

textarea:focus,

select:focus {

    outline: none;

}
```

## JS setup
==Place below code in /resources/js/app.js==
```
import "./bootstrap";

import { createApp } from "vue";

import { createWebHistory, createRouter } from "vue-router";

  

import Home from "./components/Home.vue";

  

const routes = [

    { path: "/", name: "home", component: Home },

];

  

const router = createRouter({

    history: createWebHistory(),

    routes,

});

  

const app = createApp({}).use(router).mount("#app");
```

## Vue page setup
***Rename ExampleComponent.vue to Home.vue***
===Located in /resources/js/components/===
===Place below code in Home.vue===
```
<template>

    <h1>Hello World</h1>

</template>

<script>

export default {

    data() {},

    mounted() {},

    created() {},

    methods: {},

    watch: {},

};

</script>
```

## PHP setup
===Place below code in /routes/web.php===
```
<?php

  

use Illuminate\Support\Facades\Route;

  

/*

|--------------------------------------------------------------------------

| Web Routes

|--------------------------------------------------------------------------

|

| Here is where you can register web routes for your application. These

| routes are loaded by the RouteServiceProvider and all of them will

| be assigned to the "web" middleware group. Make something great!

|

*/

  

Route::get('/{vue_capture?}', function () {

    return view('index');

 })->where('vue_capture', '[\/\w\.-]*');
```


***Rename welcome.blade.php to index.blade.php***
===located in /resources/views/===
===Place below code in index.blade.php===
```
<!DOCTYPE html>

<html lang="{{ str_replace('_', '-', app()->getLocale()) }}">

    <head>

        <meta charset="utf-8">

        <meta name="viewport" content="width=device-width, initial-scale=1">

        <link rel="icon" href="{{ Vite::asset('resources/images/favicon.ico') }}">

        @vite(['resources/css/app.css', 'resources/js/app.js'])

        <title>[NAME-OF-WEBPAGE]</title>

    </head>

    <body class="antialiased">

        <div id="app">

            <div>

                <router-view></router-view>

            </div>

        </div>

        <div class="w-screen absolute bottom-0 text-center text-xs pb-1 text-slate-300">&copy; Copyright {{ now()->year }} [NAME-OF-DEVELOPER]</div>

    </body>

</html>
```


# Running the application
===run commands in separate terminals===
```
npm run dev

php artisan serve
```

***Now click on link in PHP terminal***
