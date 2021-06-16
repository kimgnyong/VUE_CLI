<template>
  <div class="wrap">
    <div class="list-box">
        <ul>
          <li v-for='(item, index) in propsdata' v-bind:key='item'>
            <span><input id="checkboxbol" type="checkbox" v-on:change='checkFn(item, index)' value=''></span>
            <label>{{ item }}</label>
          </li>
        </ul>
      </div>
  </div>
</template>

<script>
export default {
  props:['propsdata'],
  data(){
    return{
      chebol: false
    }
  },
  methods:{
    checkFn(item, index){
      this.$emit('chkevtemit',item,index);
    }
  }
}
</script>

<style scoped>
.wrap {width:100%;}
.wrap .list-box {width:100%;}
.wrap .list-box > ul {margin:0px 10px;width:auto;text-align: left;}
.wrap .list-box > ul > li {background:#fff;margin:3px 0;line-height:45px;width:100%;display: flex;}
.wrap .list-box > ul > li > span {margin: 0 10px;}
.wrap .list-box > ul > li > span > input[type='checkbox'] {}
.wrap .list-box > ul > li > label {color:#555;text-overflow: ellipsis;overflow: hidden;width:100%;white-space: nowrap;font-size: 15px;padding-right:10px;}
</style>