<script setup>
import { onMounted } from 'vue';


</script>

<script>
export default {
  data() {
    return {
      textValue :'',
      checkValue :'',
      arr:[],
      rule:'1',
     
    };
    

  },
  mounted(){
      if(localStorage.getItem('arr')){
      this.arr = JSON.parse(localStorage.getItem('arr'));
    }
    },
  computed:{
    filterCheck() {
      if (this.rule === '1') {
        
        return this.arr;
      } else if (this.rule === '2') {
        
        return this.arr.filter(e => e.check === true);
      } else if (this.rule === '3') {
        
        return this.arr.filter(e => e.check === false);
      }
    },
    
  },
  
  methods: {
    inputText(e){
      this.textValue = e.target.value;
     
    },
  addTodo(){
    if (this.textValue === '') {
        alert('請輸入事項');
        return;
    }
    const id =  this.arr.length>0 ? this.arr[this.arr.length - 1].id : 0;
    if(this.arr.length == 0 ){
      
      const addText = {
          id : id ,
          check: false,
          text: this.textValue,
      }
      this.arr.push(addText);
    }else
    {
      const addText = {
          id : id + 1,
          check: false,
          text: this.textValue,
         
      }
      this.arr.push(addText); 
    } 
    localStorage.setItem('arr', JSON.stringify(this.arr));
    
  },
  remove(index) {
     
     this.arr.splice(index, 1);
     localStorage.setItem('arr', JSON.stringify(this.arr));
   },
   checkBtn(e){
      this.checkValue = e;
    },
    
    add1(){
      this.rule = '1';
    },
    add2(){
      this.rule = '2';
    },
    add3(){
      this.rule = '3';
    },
    addBtn1(){
      this.checkBtn();
      this.add1();
    },
    addBtn2(e){
      this.checkBtn(e);
      this.add2();
      
    },
    addBtn3(e){
      this.checkBtn(e);
      this.add3();
    },
    mapText(e){
      const content =  prompt('修改文字');
     if(content == ''){
      alert('輸入内容不能爲空');
      return;
     } 
     e.text = content;
    //   this.arr.map((item)=> {
      
    //   item.text = content;
    //     console.log(item);

    // }) ;
    localStorage.setItem('arr', JSON.stringify(this.arr));
        },
    checkTodo(e){
      // this.arr.map((item)=> {
      //     item.check = !item.check;
      // });
      e.check = !e.check;
      localStorage.setItem('arr', JSON.stringify(this.arr));
    },
  },
};

</script>

<template>

  <div class="h-screen w-screen flex justify-center">
   
    <div class="w-3/5 h-screen bg-gray-400 border-4 border-gray-900 flex items-center flex-col">
    <h1 class="mt-20 text-5xl">Todolist</h1>
    <div class="flex flex-col border-4 p-8 mt-4 border-gray-900">
    <div class="add">
      
      <input type="text" id="" class="add-text" @change = "(e) =>inputText(e)">
     
      <button class="add-Todo ml-4 rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button" @click="addTodo()">新增</button>
    </div>
    <div class="search-btn mt-8">
      <button class="all rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="all" :class="{'active':rule === '1'}" @click="addBtn1()">全部</button>
      <button class="is-todo rounded bg-slate-300 ml-4 mr-4 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="isTodo" :class="{'active':rule === '2'}" @click="addBtn2()">已執行</button>
      <button class="not-todo rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="notTodo" :class="{'active':rule === '3'}" @click="addBtn3()">未執行</button>
    </div>
  </div>

    <table class="todo mt-8">
      <thead>
        <tr>
          <th class="px-20">執行</th>
          <th class="px-20">事項</th>
          <th class="px-20">功能</th>
        </tr>
      </thead>
      <tbody class="data-show " v-for="(e,index) in  filterCheck" :key="e.id">
            <tr >
              <td><input type="checkbox" class="pl-20 ml-24" :checked="e.check" @click="checkTodo(e)"></td>
              <td class="px-20">{{ e.text }}</td>
            
            <td class="pl-20 ">
              <button class="mr-4 bg-slate-300 border-indigo-500 border-2 rounded hover:bg-sky-500" type="button" @click="mapText(e)">編輯</button>
              <button class="bg-slate-300 border-indigo-500 border-2 rounded hover:bg-sky-500" type="button" @click="remove(index)">刪除</button>
            </td>
          </tr>
          </tbody>
      
    </table>
  </div>
</div>
  


</template>

<style scoped>
.active {
  @apply bg-blue-700 text-black;
}
</style>
