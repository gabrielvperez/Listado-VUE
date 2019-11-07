<template>
  <div id="app" class="container">
    <div class="row">
      <!-- 
      <div class="col s12 m4 logotype">
        <img src="./assets/images/popcorn.png"/>
      </div>
      -->
      <div class="col s12 m12">
        <form-item :item="item" @cancel="cancel" @save="save"></form-item>
      </div>
    </div>

    <div class="row">
      <div class="col s12">
          <list :items="items" :editing="editing" @edit="edit" @remove="remove"></list>
      </div>
    </div>
  </div>
</template>



<script>
  import List from "./components/List";
  import FormItem from "./components/FormItem";
  import Filters from "./filters/filters.js"
  // import ItemMock from "./mocks/item.js"

  const ItemMock = {  
    description: null,
    viewed: false
  };

  export default {
    name: 'app',

    components: {
      List,
      FormItem,
    },


    data() {
      return {
        id: 3,
        editing: false,
        item: Object.assign({}, ItemMock),
        items: [
          {
            id: 1,
            title: 'Titanic',
            description: 'Un barco, se hunde.',
            viewed: false,
          },
          {
            id: 2,
            title: 'Ocean\'s Eleven',
            description: 'Unos ladrones, roban.',
            viewed: false,
          },
        ]
      }
    },

    mounted() {
      let scripts = [
        'https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/js/materialize.min.js'
      ]
      for (var i = 0, len = scripts.length; i < len; i++) {
        let script = document.createElement('script');
        script.setAttribute('src', scripts[i]);
        document.head.appendChild(script) ;
      }
      console.log(
        `%c GABRIEL VALERO %c`,
        'background:#35495e ; padding: 1px; border-radius: 3px 0 0 3px;  color: #fff',
        'background:#41b883 ; padding: 1px; border-radius: 0 3px 3px 0;  color: #fff'
      );
    },

    methods: {

      cancel() {
        this.item = Object.assign({}, ItemMock);
        this.editing = false;
      },

      edit(_item) {
        this.item = Object.assign(this.item, _item);
        this.editing = true;
      },
      
      save(_item) {
        if (_item.title != '' || _item.description != '') {

          if(_item.id) {
            // Edited item
            let index = this.items.findIndex(_element => _element.id === _item.id);
            this.items.splice(index, 1, _item);

          } else {
            // New item
            this.items.push({
              id: this.id++, 
              title: _item.title, 
              description: _item.description,
              viewed: _item.description.viewed
            });
          }

          this.editing = false;
          this.item = Object.assign({}, ItemMock);
        }
      },

      remove(_item) {
        let index = this.items.findIndex(_element => _element.id === _item.id);
        this.items.splice(index, 1);        
      },
    },
  }
</script>



<style type="scss" lang="css">
  /* Materialize */
  @import 'https://cdnjs.cloudflare.com/ajax/libs/materialize/1.0.0/css/materialize.min.css';
  @import 'https://fonts.googleapis.com/icon?family=Material+Icons';

  .logotype img{ 
      width: 80%;
      height: auto;
  }
  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateX(30px);
  }
  .buttons a {
    margin-right: 0px !important;
  }
  .buttons a.disabled {
    opacity: 0.3;
    cursor: auto;
  }
  .viewed-buttons a.disabled {
    opacity: 0.3;
    cursor: auto;
  }
</style>
