<script>
export default {
  data() {
    return {
      count: 0,
      className: 'red',
      inputType: 'password',
      inputBoolean: true,
      textValue: '',
      newTextValue: '',
      checkboxValue: '',
      mixCheckboxValue: [],
      mixRadioValue: '',
      fileData: '',
      show:false,
      rule:'',
    };
  },
  methods: {
    addCount() {
      this.count++;
    },
    // 改顏色
    changeColor() {
      if (this.className == 'blue') {
        this.className = 'red';
      } else {
        this.className = 'blue';
      }
    },
    // 切換input型態
    changeType() {
      // if (this.inputType == 'password') {
      //   this.inputType = 'text';
      // } else {
      //   this.inputType = 'password';
      // }
      this.inputBoolean = !this.inputBoolean;
    },
    // 獲取input裡的值
    getInputValue(e) {
      this.textValue = e.target.value;
      console.log(this.textValue);
    },
    // 上傳檔案
    uploadFile(e) {
      if (!e.target.files.length) return;
      // const file = e.target.files[0];
      if (e.target.files[0].type.includes('image/')) {
        this.fileData = e.target.files[0];
        // console.log(this.fileData);
        const img = URL.createObjectURL(this.fileData);
        this.fileData = img;
      }
    }
  },
};
</script>

<template>
  <div class="flex flex-col gap-y-2">
    <!-- <h1 class="text-8xl font-bold">{{ count }}</h1> -->

    <!-- v-on事件 -->
    <!-- <button type="button" v-on:click="count++" class="border hover:bg-slate-500">按我</button> -->
    <!-- <button type="button" @click="addCount()" class="border hover:bg-slate-500">按我</button> -->

    <!-- v-bind -->
    <!-- <div v-bind:class="className"></div> -->
    <!-- <input :type="inputType" class="text-black"> -->
    <!-- 練習 -->
    <!-- <button type="button" @click="changeColor(), addCount()" class="p-1 border hover:bg-slate-500">
      點我變色並增加Count
    </button>
    <div :class="className" class="flex justify-center items-center text-3xl">
      {{ className === 'blue' ? '藍色' : '紅色' }}
    </div> -->
    <!-- 顯示/關閉密碼 -->
    <!-- <button type="button" class="p-1 border hover:bg-slate-500" @click="changeType()">
      {{ inputBoolean ? '顯示' : '關閉' }}
    </button> -->

    <!-- <input :type="inputBoolean ?  'password' : 'text'" class="text-black" @change = "(e) => getInputValue(e)">
    <div>{{ textValue }}</div> -->

    <!-- v-model 和@input有相同功能 雙向綁定-->
    <input type="text" v-model="newTextValue" class="text-black">
    <div>{{ newTextValue }}</div>
    <!-- <input type="checkbox" :true-value = "1" :false-value = "0" v-model="checkboxValue">
    <div class="text-white">{{ checkboxValue }}</div> -->

    <!-- 多選 -->
    <div>
      1 : <input type="checkbox" :value="1" v-model="mixCheckboxValue">
      2 : <input type="checkbox" :value="2" v-model="mixCheckboxValue">
      3 : <input type="checkbox" :value="3" v-model="mixCheckboxValue">
    </div>

    <div class="text-white">{{ mixCheckboxValue.join() }}</div>

    <!-- v-model Radio -->
    <div>
      <label>
        男 : <input type="radio" v-model="mixRadioValue" value="男">
      </label>
      <label>
        女 : <input type="radio" v-model="mixRadioValue" value="女">
      </label>
      <label>
        其他 : <input type="radio" v-model="mixRadioValue" value="其他">
      </label>
    </div>
    <div>{{ mixRadioValue }}</div>

    <input type="file" multiple @change="uploadFile">
    <!-- <div>{{ fileData.name }}</div> -->
    <img :src="fileData" alt="圖片">

    <!-- v-show -->
    <!-- <div v-show = "show" >v-show 出現</div>
    <div v-if = "show" > v-if</div>
    <div v-else > v-else</div> -->
    
    <div v-if = "rule === 'if' " > {{rule}}</div>
    <div v-else-if="rule === 'else-if'">{{ rule }}</div>
    <div v-else >沒有東西</div>

    <!-- v-bind -->
    <div class="w-[100px] h-[100px]" :class="show ? 'bg-red-500' :'bg-blue-500'"></div>
    <div class="w-[100px] h-[100px] bg-blue-500" :class="{' text-yellow-500':show ,'text-5xl':rule === ''}">789</div>

  </div>
</template>

<style scoped>
.red {
  width: 100px;
  height: 100px;
  background-color: red;
}

.blue {
  width: 100px;
  height: 100px;
  background-color: blue;
}
</style>