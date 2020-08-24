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
    box-sizing: border-box;
    font-family: 'Raleway', sans-serif;
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

  .left-0{
    left: 0;
  }

  .left-25{
    left: 25%;
  }

  .left-50{
    left: 50%;
  }

  .left-75{
    left: 75%;
  }

  .left-100{
    left: 100%;
  }

  .top-0{
    top: 0;
  }

  .top-25{
    top: 25%;
  }

  .top-50{
    top: 50%;
  }

  .top-75{
    top: 75%;
  }

  .top-100{
    top: 100%;
  }

  .h-100vh {
    height: 100vh;
  }

  .color-salmon {
    color: salmon;
  }
  
  .color-dark-gray {
    color: #525252;
  }
</style>
