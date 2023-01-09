<template>
  <div class="hello">
    <button @click="searchCat"> test </button><br>
    <img style="max-width: 600px; max-height: 400px" :src="imgLink">
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data (){
    return {
      imgLink:''
    }
  },
  methods:{
    async searchCat (){
      let response = await fetch("https://api.thecatapi.com/v1/images/search");

      if (response.ok) { // if HTTP-status is 200-299
                         // obtenir le corps de réponse (la méthode expliquée ci-dessous)
        let json = await response.json();
        this.imgLink = json[0].url
        console.log(json[0].url)
      } else {
        alert("HTTP-Error: " + response.status);
      }

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
