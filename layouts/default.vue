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

  .h-10vh {
    height: 10vh;
  }

  .h-20vh {
    height: 20vh;
  }

  .h-30vh {
    height: 30vh;
  }

  .h-40vh {
    height: 40vh;
  }

  .h-50vh {
    height: 50vh;
  }

  .h-60vh {
    height: 60vh;
  }

  .h-70vh {
    height: 70vh;
  }

  .h-80vh {
    height: 80vh;
  }

  .h-90vh {
    height: 90vh;
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

  .w-10 {
    width: 10%;
  }

  .w-20 {
    width: 20%;
  }

  .w-30 {
    width: 30%;
  }

  .w-40 {
    width: 40%;
  }

  .w-60 {
    width: 60%;
  }

  .w-70 {
    width: 70%;
  }

  .w-80 {
    width: 80%;
  }

  .w-90 {
    width: 90%;
  }

  .list-style-none {
    list-style: none;
  }

  .numbers {
    font-family: 'Roboto', sans-serif !important;
    font-weight: 400;
  }
</style>
