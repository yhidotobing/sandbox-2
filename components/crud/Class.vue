<template>
  <div class="card">
    <div class="card-body">
      <form @submit.prevent="submitData">
        <InputText name="Nama Kelas" :val="form.name" @get="(newValue) => (this.form.name = newValue)" />
        <InputText
          name="Deskripsi Kelas"
          :val="form.description"
          @get="(newValue) => (this.form.description = newValue)"
        />
        <InputText
          name="Tanggal Mulai"
          type="date"
          :val="form.startDate"
          @get="(newValue) => (this.form.startDate = newValue)"
        />
        <InputText
          name="Tanggal Selesai"
          type="date"
          :val="form.endDate"
          @get="(newValue) => (this.form.endDate = newValue)"
        />
        <div class="text-right">
          <button type="button" class="btn btn-secondary mr-3" @click="$router.go(-1)">Cancel</button>
          <button type="submit" class="btn btn-primary">Submit</button>
        </div>
      </form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    const detailClass = this.$store.state.class.class;
    return {
      form: detailClass,
    };
  },
  created() {
    if (this.$route.params.id) {
      this.getDetail();
    }
  },
  methods: {
    async getDetail() {
      try {
        const response = await this.$axios.get(`/class/${this.$route.params.id}`);
        this.form = response.data.data;
      } catch (error) {
        console.log(error);
      }
    },
    async tambahKelas() {
      const payload = this.form;
      try {
        const response = await this.$axios.post("/class", payload);
        alert("Data berhasil ditambahkan");
        this.$router.push("/class");
      } catch (error) {
        console.log(error);
      }
    },
    async updateKelas() {
      const payload = this.form;
      try {
        const response = await this.$axios.put(`/class`, payload);
        alert("Data berhasil diupdate");
        this.$router.push("/class");
      } catch (error) {
        console.log(error);
      }
    },
    async submitData() {
      if (this.$route.params.id) {
        await this.updateKelas();
      } else {
        await this.tambahKelas();
      }
    },
  },
};
</script>
