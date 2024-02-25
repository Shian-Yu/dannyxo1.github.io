<script setup>
</script>

<template>
  <main>
    <div class="box-big w-full h-screen flex justify-center items-center">
      <div class="w-[75%] h-[75%] flex justify-center items-center bg-slate-400 flex-col p-5">
        <div class="write w-full h-[10%]">
            <input type="text" placeholder="請輸入事項" class="input-text add-text w-[75%]">
            <button class="add-Todo">新增</button>
        </div>
        <div class="title-all w-full h-[10%] flex gap-3">
            <button class="all title bg-slate-300 hover:bg-slate-100" data-search="all">全部</button>
            <button class="is-todo title bg-slate-300 hover:bg-slate-100" data-search="isTodo">已執行</button>
            <button class="not-todo title bg-slate-300 hover:bg-slate-100" data-search="notTodo">未執行</button>
        </div>
        <div class="content-all w-full h-[70%]">
            <div class="content flex justify-around ">
                <div class="m1 w-1/3">執行</div>
                <div class="m1 w-1/3">事項</div>
                <div class="ma w-1/3">功能</div>
            </div>
            <div class="data-show">
                <div class="content flex justify-around">
                    <div class="m1 w-1/3">
                        <input type="checkbox">
                    </div>
                    <div class="m1 w-1/3">第一筆</div>
                    <div class="btn-box w-1/3 m1 flex gap-2">
                        <button class="content-btn bg-slate-200">編輯</button>
                        <button class="content-btn bg-slate-200">刪除</button>
                    </div>
                </div>
            </div>
            <button class="enter-to-local bg-slate-200" type="button">存進local</button>
        </div>
      </div>
    </div>
  </main>
</template>
