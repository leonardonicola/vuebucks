<template>
  <div id="app">
    <Header/>
    <Home/>
    <Coffee/>
    <div class="circle"></div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Home from './components/Home.vue'
import Coffee from './components/Coffee.vue'
export default {
  components:{Header, Home, Coffee}
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Archivo:wght@400;700;900&display=swap');
*{
  box-sizing: border-box;
  font-family: 'Archivo', sans-serif;
}

body,html{
  position: relative;
  margin:0
}

.circle{
  position: absolute;
  top: -300px;
  right: 30vh;
  width: 750px;
  height: 750px;
  border-radius: 50%;
  background-color: rgb(101, 202, 169);
  z-index: -3;
  opacity: .15;
}
</style>