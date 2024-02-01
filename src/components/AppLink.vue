<script>
import {RouterLink} from 'vue-router'
export default{
  props: { ...RouterLink.props },
  computed:{
    isExternal(){
      return typeof this.to === 'string' && this.to.startsWith('http')
    }
  }
}
</script>

<template>
  <a 
    :href="to" 
    target="_blank"
    rel="noopener"
  >
    <slot/>
  </a>
</template>
