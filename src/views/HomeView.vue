<script setup>

</script>

<script>
export default {
  data() {
    return {
      textValue :'',
      checkValue :'',
      arr:[],
      rule:'0',
        
      
    };
  },
  computed:{
    filterCheck(){
        if(!this.checkValue){
          return this.arr;
        }
        return this.arr.filter(e => e.check === this.checkValue);
      },
  },
  
  methods: {
    inputText(e){
      this.textValue = e.target.value;
     
    },
  addTodo(){
    
    if(this.arr.length == 0 ){
      const id = 1;
      const addText = {
          id : id ,
          check: 'false',
          text: this.textValue,
      }
      this.arr.push(addText);
    }
    else
    {const id = this.arr[this.arr.length - 1].id;
      const addText = {
          id : id + 1,
          check: 'false',
          text: this.textValue,
         
      }
      this.arr.push(addText); 
    } 
      

  },
  remove(index) {
     
     this.arr.splice(index, 1);
   },
   checkBtn(e){
      this.checkValue = e;
    },
    mapText(e){
      const content =  prompt('修改文字');
     
    //   this.arr.map((item)=> {
      
    //   item.text = content;
    //     console.log(item);

    // }) ;
        e.text = content;
   
        
    },
    checkTodo(e){
      // this.arr.map((item)=> {
      //     item.check = !item.check;
      // });
      e.check = !e.check;
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
      <button class="all rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="all" @click="checkBtn('')">全部</button>
      <button class="is-todo rounded bg-slate-300 ml-4 mr-4 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="isTodo" @click="checkBtn('true')">已執行</button>
      <button class="not-todo rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="notTodo" @click="checkBtn('false')">未執行</button>
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
      <tbody class="data-show" v-for="(e, index) in  filterCheck" :key="index">
            <tr >
              <td><input type="checkbox" class="pl-20" @click="checkTodo(e)"></td>
              <td class="px-20">{{ e.text }}</td>
            
            <td class="pl-20">
              <button type="button" @click="mapText(e)">編輯</button>
              <button type="button" @click="remove(index)">刪除</button>
            </td>
          </tr>
          </tbody>
      
    </table>
  </div>
</div>
  


</template>
