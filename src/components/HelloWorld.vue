<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <tab></tab>
    <p>
      编辑器
    </p>
    <input v-model="text" type="text" @keyup.enter="onSubmit">
    <ul>
      <li v-for="(item,index) in list" v-bind:key="item.Date">{{index+1}}---{{item.text}}---{{item.Date}}</li>
    </ul>
    <footerTab></footerTab>
  </div>
</template>

<script>
import { tab } from '@/components'
import qs from "qs"
import footerTab from "@/components/footer/footer";

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  components:{
    tab,
    footerTab
  },
  data(){
    return{
      text:"",
      list:[],
    }
  },
  mounted() {

    let string = 'a[b][c][d][e][f][g][h][i]=j';
    console.log(qs.parse(string))
  },
  methods:{
    onSubmit(){
      this.list.push({
        text:this.text,
        Date:new Date()
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin:  10px;
}
a {
  color: #42b983;
}
</style>
