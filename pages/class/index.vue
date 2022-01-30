<template>
  <div>
    <FloatingButton @click.native="$router.push('/class/add')" />
    <div class="row">
      <div v-for="(kelas, i) in listClass" :key="i" class="col-md-4">
        <NuxtLink :to="'/class/' + kelas.id">
          <BootstrapCard>
            <template v-slot:header>
              <img :src="kelas.img" alt="" style="height: 200px" />
            </template>
            <template v-slot:default>
              {{ kelas.name }}
            </template>
          </BootstrapCard>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      listClass: [],
    };
  },
  created() {
    this.getListClass();
  },
  methods: {
    async getListClass() {
      try {
        const response = await this.$axios.get("/class");
        this.listClass = response.data.data;
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
