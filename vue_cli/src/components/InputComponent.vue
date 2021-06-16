<template>
  <div class="wrap">
    <div class="input-box">
      <input type="text" v-model="newinputItem" v-on:keyup.enter='addItem' placeholder="스케줄을 입력하세요">
      <button v-on:click="addItem">추가</button>
      <button v-on:click="delItem(propsdata1,propsdata2)">삭제</button>
      <!-- 템플릿트에 발생하는 이벤트는 반드시 $emit()으로 이벤트를 생성하여 생성된 이름을 상위 컴포넌트에서 전달한다 -->
      <!-- 상위 컴포넌트는 전달받은 이벤트 이름 속성을 이용하여 상위 컴포넌트에서 메서드를 호출하여 이벤트를 수행한다. -->
    </div>
  </div>
</template>

<script>
export default {
  data(){ //데이터 메서드
    return{
      newinputItem:'',  // v-model 양방향 전송
      cnt:0
    }
  },
  props:['propsdata1','propsdata2'],
  methods:{
    addItem(){ // add 버튼 클릭 이벤트 호출 메서드
      var value = this.newinputItem;
      this.cnt++;
      this.$emit('addItem',this.cnt,value);
      this.inputText();
    },
    delItem(item,index){
      this.$emit('deleitem',item,index);
    },
    inputText(){
      this.newinputItem = ''; // 해당 내용을 작성하면 입력창의 내용 삭제하기
    }
  }
  
  
}
</script>

<style>
.wrap {width:100%;}
.wrap .input-box {width:85%;margin:0 auto;padding:15px 0;display: flex;}
.wrap .input-box > input[type='text'] {width:85%;height:50px;border: 1px solid #ccc;box-sizing: border-box;padding:0 10px;border-radius: 8px 0 0 8px;margin-right:auto;}/* 부모영역 flex  자식영역 margin-right:auto  왼쪽정렬*/
.wrap .input-box > input[type='text']::placeholder {color:#bbb;}
.wrap .input-box > button {width:60px;height:50px;border:0;background: #2c3e50;color:#fff;border-radius: 0 8px 8px 0;margin-left:auto;}/* 부모영역 flex  자식영역 margin-left:auto  오른쪽정렬*/
.wrap .input-box > button:nth-of-type(1) {border-radius: 0 0px 0px 0;}
</style>