<template>
  <div class="about">
    <button @click="getToken">gettoken</button>
  </div>
</template>
<script>
export default {
  data(){
    return {

    }
  },
  methods:{
    getToken(){
      this.$axios.get(
        '/oauth/2.0/token',
        {params:{
          grant_type:'client_credentials',
          client_id:'XdWbn0drKXZopGEEBbj409PU',
          client_secret:'x9txZVgLzW45MYvRYpknBkopKvDhRRD5'
        }}
      ).then(res=>{
        console.log(res)
      })
    }
  }
}
</script>