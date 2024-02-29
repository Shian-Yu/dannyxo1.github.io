<script>
export default {
  data() {
    return{
      todoArr: [
        {
          id: 1,
          text: 222,
          status: true,
        },
        {
          id: 2,
          text: 222,
          status: false,
        },
        {
          id: 3,
          text: 222,
          status: false,
        },
      ],
      todoText: '',
      switchArr: null,
    };
  },
  methods: {
    // 新增待辦事項
    addTodo() {
      if (this.todoText.trim() !== '') {
        const id = this.todoArr.length ? this.todoArr[this.todoArr.length - 1].id : 0;
        const addArr = {
          id: id + 1,
          text: this.todoText,
          status: false,
        }
        this.todoArr.push(addArr);
        this.todoText = '';
      } else {
        alert('請輸入待辦事項');
      }
    },
    // 編輯待辦事項
    editText(index) {
      const newText = prompt('請輸入修改後的文字');
      this.todoArr[index].text = newText;
    },
    // 刪除待辦事項
    deleteText(index) {
      if(confirm('確定要刪除?')){
        this.todoArr.splice(index,1);
      }
    },
  },
  computed: {
    // 篩選待辦事項
    filterArr () {
      if (this.switchArr === null){
        return this.todoArr;
      } else {
        return this.todoArr.filter(item => item.status === this.switchArr);
      };
    },
  },
};
</script>

<template>
  <main>
    <div class="box-big w-full flex justify-center items-center mt-10">
      <div class="w-[75%] h-[75%] flex items-center bg-slate-400 flex-col p-5">
        <div class="write w-full h-[5%] flex justify-center items-center gap-2 mb-2">
          <input v-model="todoText" type="text" placeholder="請輸入事項" class="input-text add-text w-[75%]">
          <button class="add-Todo bg-slate-200 p-2" @click="addTodo">新增</button>
        </div>
        <div class="title-all w-full flex">
          <button class="all title p-2 border border-black bg-slate-300 hover:bg-slate-100" :class="{'bg-slate-50' : switchArr === null}" @click="switchArr = null">全部</button>
          <button class="is-todo title p-2 border border-black bg-slate-300 hover:bg-slate-100"
            :class="{'bg-slate-50' : switchArr === true}" @click="switchArr = true">已執行</button>
          <button class="not-todo title p-2 border border-black bg-slate-300 hover:bg-slate-100"
            :class="{'bg-slate-50' : switchArr === false}" @click="switchArr = false">未執行</button>
        </div>
        <div class="content-all w-full border-t-4 border-black border-b-2 p-2">
          <div class="content flex justify-around">
            <div class="m1 w-1/3 text-center">執行</div>
            <div class="m1 w-1/3 text-center">事項</div>
            <div class="ma w-1/3 text-center">功能</div>
          </div>
          <div class="data-show w-full">
            <div v-for="(item,index) in filterArr" :key="item.id" class="content flex justify-around text-center border-t border-gray-500 mt-2 pt-2">
              <div class="m1 w-1/3">
                <input v-model="item.status" type="checkbox">
              </div>
              <div class="m1 w-1/3">第{{ item.id }}筆, {{ item.text }}</div>
              <div class="btn-box w-1/3 m1 flex gap-4 justify-center p-2">
                <button class="content-btn bg-slate-200" @click="editText(index)">編輯</button>
                <button class="content-btn bg-slate-200" @click="deleteText(index)">刪除</button>
              </div>
            </div>
          </div>
          <div class=" border-t-2 border-black p-2">
            <button class="enter-to-local bg-slate-200" type="button">存進local</button>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
