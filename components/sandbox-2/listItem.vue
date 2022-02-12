<template>
  <div>
    <ul class="list-group list-group-flush">
      <li
        v-for="(item, i) in items"
        :key="i"
        class="list-group-item d-flex justify-content-between"
      >
        <div class="form-check">
          <input
            class="form-check-input"
            type="checkbox"
            @change="checkItem(item)"
          />
          <label class="form-check-label" :for="item">
            {{ item }}
          </label>
        </div>
        <button type="button" @click="clickDelete(i)" class="btn btn-danger">
          <i class="fas fa-trash"></i>
        </button>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },

  methods: {
    clickDelete(index) {
      const newValue = this.items.filter((item, i) => i !== index);
      this.$emit("get", newValue);
    },
    checkItem(item) {
      const newValue = this.items.map((item) => {
        if (item === this.items[this.items.indexOf(item)]) {
          return item;
        } else {
          return "";
        }
      });
      this.$emit("get", newValue);
      this.listDone.push(item);
    },
  },
};
</script>
