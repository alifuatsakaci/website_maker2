<template>
    <!-- Default layout wrapper -->
    <div class="layout-default">
      <!-- Render the page component -->
      <NuxtPage />
    </div>
  </template>
  
  <script setup>
  // Default layout logic (if any) goes here
  </script>
  
  <style>
  /* Make entire app fill the viewport with no frame */
  html, body, #__nuxt, .layout-default {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
  }
  
  .layout-default {
    background-color: #F8F8F8;
  }
  </style>
  