<script setup>
import {computed, reactive} from "vue";
const  properties = reactive({
  perspective:100,
  rotateX:0,
  rotateY:0,
  rotateZ:0
})
const bgColor=reactive({
  red:0,
  green:0,
  blue:0
})
const boxColor= computed(() => {
  return {
    backgroundColor: `rgb(${bgColor.red},${bgColor.green},${bgColor.blue})`
  }
  
})
const box= computed(() => {
  return{
    transform:`
    perspective(${properties.perspective}px)
    rotateX(${properties.rotateX}deg) 
    rotateY(${properties.rotateY}deg) 
    rotateZ(${properties.rotateZ}deg)
    `
  }
})
const reset =() => {
  properties.perspective = 100;
  properties.rotateX = 0;
  properties.rotateY = 0;
  properties.rotateZ = 0;
}
</script>

<template>
 
<div>
  <h2>Css3 Perspective Playground</h2>
 <main>
  <section class="setting">
    <div class="setting-container">
      <label >Perspective:{{properties.perspective}}px;</label>
      <input type="range" min="0" max="999" v-model="properties.perspective">
      <label> rotateX: {{ properties.rotateX }}deg;</label>
      <input type="range" min="0" max="360" v-model="properties.rotateX">
      <label> rotateY: {{ properties.rotateY }}deg;</label>
      <input type="range" min="0" max="360" v-model="properties.rotateY">
      <label> rotateZ: {{ properties.rotateZ }}deg;</label>
      <input type="range" min="0" max="360" v-model="properties.rotateZ">

      <button @click="reset">Reset</button>
    </div>

  </section>
  <section class="output">
    <div class="output-container">
      <div class="box" :style="[box,boxColor]"></div>
    </div>
  </section>
  <section class="box-color">
    <p class="myColor" :style="boxColor">Change Background color</p>
    <div>
      <label>Red:{{ bgColor.red }}</label>
      <input type="range" min="0" max="255" v-model="bgColor.red">
      <label>Green:{{ bgColor.green }}</label>
      <input type="range" min="0" max="255" v-model="bgColor.green">
      <label>Blue:{{ bgColor.blue }}</label>
      <input type="range" min="0" max="255" v-model="bgColor.blue">
    </div>
  </section>
 </main>
</div>
</template>

<style scoped>
.myColor{
  font-size: 20px;
  font-weight: bold;
  color:aliceblue;
  padding: 10px;
  margin-top: -20px;
}
</style>
