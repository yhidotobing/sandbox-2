<template>
  <div>
    <div class="card">
      <div class="card-body">
        <h3 class="text-center">Sandbox Frontend 2</h3>
        <div class="d-flex justify-content-center">
          <div class="col-md-4">
            <Sandbox-2Add @get="(newValue) => this.todoList.push(newValue)" />
            <br />
            <p>To do List :</p>
            <Sandbox-2ListItem
              :items="todoList"
              @get="(newValue) => (this.todoList = newValue)"
            />
            <p v-for="(item, i) in listDone" :key="i">List Done : {{ item }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  layout: "clear",
  auth: false,
  data() {
    return {
      todoList: ["Tidur"],
    };
  },
};
</script>
