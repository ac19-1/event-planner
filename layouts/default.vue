<template>
  <div>
    <Nuxt />
  </div>
</template>

<style>
  html{
    overflow-y: auto !important;
    scroll-behavior: smooth;
    background-color: transparent;
  }

  * {
    margin: 0;
    padding: 0;
  }

  ::-webkit-scrollbar{
    width: 8px;
  }
  ::-webkit-scrollbar-track{
    background: #dddddd;
  }
  ::-webkit-scrollbar-thumb{
    background: #777777;
    border-radius: 8px;
  }
  ::-webkit-scrollbar-thumb:hover{
    background: #646464;
  }
</style>
