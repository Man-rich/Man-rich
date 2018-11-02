<template>
  <div id="app">
    <Come></Come>
    <div id="main">
    	<router-view/>
    </div>
  </div>
</template>

<script>
	import Come from '@/components/init'
export default {
  name: 'App',
  components:{
  	Come
  }
}
</script>

<style>

</style>
