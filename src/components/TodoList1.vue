<template>
  <div class="card">
    <div class="card-body p-2">
      <div class="d-flex" v-for="i in todos" :key="i.id">
        <div class="form-check flex-grow-1">
          <label class="form-check-label" :class="{ tolist: i.completed }"> <input type="checkbox" class="form-check-input" v-model="i.complated" />{{ i.subject }}</label>
        </div>
        <div>
          <button class="btn btn-danger btn-sm" @click="deleteTodo(i)">삭제</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },

  //setup(props) {},
};
</script>

<style></style>
