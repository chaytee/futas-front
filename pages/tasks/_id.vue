<template>
<div class="edit-block">
  <h2 class="mb-3">mission Edit</h2>
  <div class="btn__wrap">
    <button class="btn__grade" @click="editClose">一覧へ戻る</button>
  </div>
  <!-- taskのidを子コンポーネントに渡す　プロップスで渡すときはハイフンが好ましいtask-id data渡すとき:つける-->
  <TaskForm :task-id="$route.params.id" />
</div>
</template>
<script>
import TaskForm from "../../components/TaskForm";
export default {
  async asyncData({app, params}) {
    const url = `api/users/tasks/${params.id}`;

    const response =  await app.$axios.get(url);

    console.log(response);
    return
  },
  components: {
    TaskForm
  },
  data() {
    return {
      task: [],
      isActive: false,
    };
  },
  methods: {
    editClose() {
      this.$router.push("/tasks");
    }
  },
};
</script>
<style lang="scss">
  .edit-block {
    padding: 20px 0;
    .task-form {
      margin-top: 20px;
    }
  }
</style>
