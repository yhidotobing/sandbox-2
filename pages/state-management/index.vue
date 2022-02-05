<template>
  <div>
    <h2>{{ $store.state.class.title }}</h2>
    <FloatingButton @click.native="$router.push('/class/add')" />
    <div class="row">
      <div v-for="(kelas, i) in listClass" :key="i" class="col-md-4">
        <!-- <NuxtLink :to="'/class/' + kelas.id"> -->
        <BootstrapCard @click.native="setDetailClass(kelas)">
          <template v-slot:header>
            <img :src="kelas.img" alt="" style="height: 200px" />
          </template>
          <template v-slot:default>
            {{ kelas.name }}
          </template>
        </BootstrapCard>
        <!-- </NuxtLink> -->
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      //   listClass: this.$store.state.class.classes,
    };
  },
  computed: {
    listClass() {
      return this.$store.state.class.classes;
    },
  },
  created() {
    this.getListClass();
  },
  methods: {
    async getListClass() {
      try {
        const response = await this.$axios.get("/class");
        // this.listClass = response.data.data;
        this.$store.dispatch("class/SET_CLASSES", response.data.data);
      } catch (error) {
        console.log(error);
      }
    },
    setDetailClass(kelas) {
      this.$store.dispatch("class/SET_CLASS", kelas);
      this.$router.push("/class/" + kelas.id);
    },
  },
};
</script>
