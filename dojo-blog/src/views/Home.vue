<template>
  <div class="home">
    <h1>Home</h1>

    <input type="text" v-model="search">
    <p>search term - {{search}}</p>
    <div v-for="name in matchingNames" :key="name">{{name}}</div>
    <button @click='handelClick'>Stop watching</button>
  </div>
</template>

<script>
import {ref,computed,watch,watchEffect} from 'vue'

export default {
  name: 'Home',

  setup(){
    const search = ref('')
    const names = ref(['mario','yoshi','luigi','toad','bowser','koopa','peach'])
    
    const stopwatch = watch(search,()=>{
      console.log('watch function run')
    })
    const stopWatchEffect = watchEffect(()=>{
      console.log('watchEffect funtion run', search.value)
    })
    const matchingNames = computed(()=>{
      return names.value.filter((name)=>name.includes(search.value))
    })
    const handelClick=()=>{
      stopwatch();
      stopWatchEffect()
    }
    return { names, search,matchingNames,handelClick }
  }
}
</script>
