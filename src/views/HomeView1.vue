

<script>
export default {
  data() {
    return {
      num: 1,
      arr: [
        {
          id: 1,
          name: '张三',
          idnumber: 'P12345678',
          sex: '男',
          phone: '0987654321',
        },
        {
          id: 2,
          name: '张三',
          idnumber: 'P12345678',
          sex: '男',
          phone: '0987654321',
        },
        {
          id: 3,
          name: '张三',
          idnumber: 'P12345678',
          sex: '女',
          phone: '0987654321',
        },
        {
          id: 4,
          name: '张三',
          idnumber: 'P12345678',
          sex: '女',
          phone: '0987654321',
        },

      ],
      selectedTab:'',
    };
  },
  computed:{
    // getNum(){
    //   return this.num / 2;
    // }
      filterUserDate(){
        if(!this.selectedTab){
          return this.arr;
        }
        return this.arr.filter(item => item.sex === this.selectedTab);
      }

  },
  mounted(){
      
  },
  methods: {

    remove(index) {
     
      this.arr.splice(index, 1);
    },
    changeSex(item){
      this.selectedTab = item;
    },
  }
};
</script>



<template>
  <!-- {{ getNum }} -->
  <!-- <div v-for="(item,index) in 99" :key="index" class="text-3xl text-white border border-white">
  {{ index }}
  </div> -->
  <!-- <button type="button" @click="add()" class="text-white">新增</button>
  <button type="button" @click="remove()" class="text-white">刪除</button> -->

  <!-- <div v-for="(item,index) in arr" :key="index" class="text-3xl text-white border border-white">
  {{ item }}
  </div> -->
  <button class="text-3xl text-white" @click="changeSex('')">不限</button>
  <button class="text-3xl text-white" @click="changeSex('男')">男</button>
  <button class="text-3xl text-white" @click="changeSex('女')">女</button>
  <div class="flex justify-around text-white border border-white">
    <div class="text-3xl text-white">編號</div>
    <div class="text-3xl text-white">姓名</div>
    <div class="text-3xl text-white">身份證號</div>
    <div class="text-3xl text-white">性別</div>
    <div class="text-3xl text-white">電話</div>
    <div class="text-3xl text-white">功能</div>
  </div>
  <div>
    <div v-for="(item, index) in  filterUserDate" :key="index" class="flex  items-center justify-around text-3xl text-white border border-white">
      <div>{{ item.id }}</div>
      <div>{{ item.name }}</div>
      <div>{{ item.idnumber }}</div>       
      <div>{{ item.sex }}</div>
      <div>{{ item.phone }}</div>
      <button type="button" @click="remove(index)">刪除</button>
    </div>

  </div>
</template>