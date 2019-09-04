<template>
<div id="app" class="container">


  <div class="row">
    <div class="col s12 m4 logotype">
      <img src="./assets/images/popcorn.png"/>
    </div>
    <div class="col s12 m8">
      <add :list="list" ></add>
    </div>
  </div>

  <div class="row">
    <div class="col s12">
      <list :list="list"></list>
    </div>
  </div>


</div>
</template>

<script>
import List from "./components/List"
import Add from "./components/Add"

export default {
  name: 'app',
  components: {
    List,
    Add
  },
  data: () => {
    return {
      list: []
    }
  },
  mounted() {
    let scripts = [
      'https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js'
    ]

    for (var i = 0, len = scripts.length; i < len; i++) {
      let recaptchaScript = document.createElement('script')
      recaptchaScript.setAttribute('src', scripts[i])
      document.head.appendChild(recaptchaScript)
    }
  },
}
</script>

<style type="scss">
  /* Materialize */
  @import 'https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css';
  @import 'https://fonts.googleapis.com/icon?family=Material+Icons';

  .logotype img{ 
      width: 80%;
      height: auto;
  }
</style>