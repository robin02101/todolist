<script setup>

</script>

<template>

  <div class="h-screen w-screen flex justify-center">
    
    <div class="w-3/5 h-screen bg-gray-400 border-4 border-gray-900 flex items-center flex-col">
    <h1 class="mt-20 text-5xl">Todolist</h1>
    <div class="flex flex-col border-4 p-8 mt-4 border-gray-900">
    <div class="add ">
      <input type="text" id="" class="add-text">
      <button class="add-Todo ml-4 rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button">新增</button>
    </div>
    <div class="search-btn mt-8">
      <button class="all rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="all">全部</button>
      <button class="is-todo rounded bg-slate-300 ml-4 mr-4 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="isTodo">已執行</button>
      <button class="not-todo rounded bg-slate-300 border-indigo-500 border-2 hover:bg-sky-500" type="button" data-search="notTodo">未執行</button>
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
      <tbody class="data-show hidden">
            <tr><td><input type="checkbox" onclick="checkTodo(undefined)"></td>
            
            <td>
              <button type="button" onclick="editText(undefined)">編輯</button>
              <button type="button" onclick="deleteText(undefined)">刪除</button>
            </td></tr>
          </tbody>
      
    </table>
  </div>
</div>
  


</template>
