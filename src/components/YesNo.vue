<script setup>
	import { ref } from 'vue'
	const response = ref({})

  // adding delay
  await new Promise(resolve => {
    setTimeout(() => { 
      resolve()
    }, 1000)
  })
    
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts/' +  Math.floor(Math.random() * 10) + 1)
    console.log(res)
    response.value = (await res.json())
  } catch (error) {
    response.value = { answer: 'Error! Could not reach the API. ' + error, image: '' }
  }

</script>

<template>
  <p>Title: {{ response.title }}</p>
</template>