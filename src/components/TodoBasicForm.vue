<template>
  <form action="#" class="d-flex" @:submit.prevent="onSubmit">
    <div class="input-group mb-3">
      <input
        type="text"
        class="form-control"
        v-model="todo"
        placeholder="일정을 추가하세요"
      />
      <button class="btn btn-primary" type="submit">추가하기</button>
    </div>
    <div v-if="errMsg" class="alert alert-danger">할일을 입력해주세요</div>
  </form>
</template>

<script>
import { ref } from "vue";
export default {
  setup(props, { emit }) {
    const todo = ref("");
    const errMsg = ref(false);
    const onSubmit = () => {
      if (todo.value === "") {
        errMsg.value = true;
      } else {
        //emit('이벤트명',{전달할데이터})
        emit("add-todo", {
          id: Date.now(),
          subject: todo.value,
          completed: false,
        });
        errMsg.value = false;
        todo.value = "";
      }
    };
    return { todo, errMsg, onSubmit };
  },
};
</script>

<style>
</style>
