<template>
  <div class="hello">
    <h1>{{ msg }}</h1>


      <div class="row justify-content-center">
    <b-form-input
          id="input-1"
          v-model="search"
          type="text"
          required
          placeholder="trouble"
          class="m-2 col-11 col-sm-8  "
        ></b-form-input>
        </div>


     <div class="row m-2 justify-content-center">
      <b-card
        v-for="(value, name) in data"
        :title="name"
        :key="name"
        tag="article"
        style="max-width: 20rem;"
        class="m-2 col-12 col-sm-4"
      >
        <b-card-text>
        <b-list-group>
          <b-list-group-item button  v-on:click="solutions=item.solutions" v-b-modal.modal-1 v-for="(item,i) in value" :key="i">
            <b v-if="item.symptom.indexOf(search)>=0&&search.length>2">{{item.symptom.slice(0, item.symptom.indexOf(search))}}<span>{{item.symptom.slice( item.symptom.indexOf(search), item.symptom.indexOf(search)+search.length )}}</span>{{item.symptom.slice( item.symptom.indexOf(search)+search.length , 1000)}}</b>
            <template v-else="">{{item.symptom}}</template>
          </b-list-group-item>
        </b-list-group>
        </b-card-text>
      </b-card>
    </div>
    <b-modal id="modal-1"  ok-only  title="Solutions">
      <ul class="my-4">
        <template v-for="(item,i) in solutions" >
        <b :key=i v-if="i!=0">or</b>
        <li :key=i  class="text-capitalize"> {{item}}<br /></li>
        </template>
        </ul>
    </b-modal>

</div>
</template>

<script>

import sampleData from './sampledata.json';

export default {
  name: 'Troubles',
  data() {
     return {
      pos:0,
      solutions:"",
      data: sampleData,
       search: "",
     }
   },
  props: {
    msg: String
  }
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
    list-style-type: disc !important;
    padding-left: 1em;
}

a {
  color: #42b983;
}

span {
  background-color:yellow;
}
</style>
