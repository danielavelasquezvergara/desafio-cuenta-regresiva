<template>
<div id="app">
<h3>CUENTA REGRESIVA</h3>
  <h1>00:{{contador_seg < 10 ? '0'+contador_seg : contador_seg }} /seg</h1>
  <div class="botones">
    <!-- botones @click -->
    <button @click="iniciar(5)">5 seg</button>
    <button @click="iniciar(10)">10 seg</button>
    <button @click="iniciar(30)">30 seg</button>
    <button @click="iniciar(60)">60 seg</button>
  </div>
  
</div>
</template>

<script>
export default {
  name: "contador_regresivo",
  data() {
    return {
     
      contador_seg: 0,  //segundos
      intervalo_principal: null,
    };
  },
  methods: {
    //cediendo valor
    iniciar(time) {
      this.contador_seg = time;
      clearInterval(this.intervalo_principal);
      
      this.intervalo_principal = setInterval(() => {
        //si este contador_seg es mayor que 0, restale un segundo -- cuenta regresiva --
        this.contador_seg > 0 ? this.contador_seg-- : clearInterval(this.intervalo_principal);
      }, 1000);
    },
  },
};
</script>

<style lang="scss">
body{
  background-color: #f5f5f5;
  display: flex;
  justify-content: center;
}
#app {
  width: 500px;
  text-align: center;
  background-color: rgb(61, 45, 182);
  color: black;
  padding: 30px 0 50px 0;
  margin-top: 70px;
  font-family: 'Open sans', sans-serif;
  opacity:0.85 ;
  border-radius: 10%;
 button{
   font-family: 'Open sans', sans-serif;
   margin: 5px;
   background-color: rgb(179, 65, 224);
   color: black;
   cursor: pointer;
   border: rgb(179, 65, 224);
   
 }
 h3 {
   text-align: center;
 }
}
</style>
