<template>
  <div id="app">
    <header-component></header-component>
    <input-component v-on:addItem='addItem' v-on:deleitem='delelastFn' :propsdata1='delitem' :propsdata2='delindex'></input-component>
    <list-component v-bind:propsdata='itemArr' v-on:chkevtemit='deleFn'></list-component>
    <footer-component></footer-component>
  </div>
</template>



<script>
import HeaderCompontnt from './components/HeaderCompontnt.vue'
import InputComponent from './components/InputComponent.vue'
import ListComponent from './components/ListComponent.vue'
import FooterComponent from './components/FooterComponent.vue'

export default {
  name: 'app',
  components:{
    'header-component' : HeaderCompontnt,
    'input-component' : InputComponent,
    'list-component' : ListComponent,
    'footer-component' : FooterComponent
  },
  data(){
    return{
      itemArr:[],
      delitem:'',
      delindex:0
    }
  },
  methods:{
    addItem(cnt,value){
      localStorage.setItem(value,cnt);
      this.itemArr.push(value);  // 배열에 저장하기
      console.log(this.itemArr);
    },
    deleFn(item,index){
      this.delitem = item;
      this.delindex = index;   // 삭제버튼이 input컴포넌트에 있기때문에 한번 프롭스를 해준후 다시 에밋으로 가져온다
    },
    delelastFn(item,index){
      this.itemArr.splice(index,1);
      localStorage.removeItem(item);
    }
  },
  created(){
    for(var i=0; i<localStorage.length; i++){
      this.itemArr[i] = localStorage.key(i);
    }
  }
}
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
}
</style>
