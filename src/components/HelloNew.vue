<template>
   <p>{{greeting}}</p> 
</template>


<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'HelloNew',
    props: ['greeting']        
})
</script>
