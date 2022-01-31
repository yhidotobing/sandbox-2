<template>
  <div>
    <div class="card">
      <div class="card-body">
        <h3 class="text-center">Sandbox Frontend 1</h3>
        <div class="row">
          <div class="col-md-4">
            <SandboxAdd @get="(newValue) => this.listBuku.push(newValue)" />
            <br />
            <SandboxListItem :items="listBuku" @get="(newValue) => (this.listBuku = newValue)" />
          </div>
          <div class="col-md-4">
            <SandboxAdd @get="getPembaca" />
            <br />
            <SandboxListItem :items="listPembaca" @get="(newValue) => (this.listPembaca = newValue)" />
          </div>
          <div class="col-md-4">
            <SandboxOption
              :listPembaca="listPembaca"
              :listBuku="listBuku"
              @get="(newValue) => this.listBacaan.push(newValue)"
            />
            <br />
            <SandboxListItem :items="listBacaan" @get="(newValue) => (this.listBacaan = newValue)" />
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
      listBuku: ["Buku 1", "Buku 2"],
      listPembaca: ["Pembaca 1", "Pembaca 2"],
      listBacaan: ["Pembaca 1 - Buku 1", "Pembaca 2 - Buku 2"],
    };
  },
  methods: {
    getPembaca(newValue) {
      this.listPembaca.push(newValue);
    },
  },
};
</script>
