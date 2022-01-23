<template>
  <div>
    <div class="row">
      <div v-for="(kelas, i) in listClass" :key="i" class="col-md-4">
        <NuxtLink :to="'/class/' + kelas.link">
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
      listClass: [
        {
          name: "Kelas React JS",
          img: "https://glints.com/id/lowongan/wp-content/uploads/2020/10/logo-reactjs.jpg",
          link: "react-js",
        },
        {
          name: "Kelas Vue JS",
          img: "https://crocodic.com/wp-content/uploads/2019/02/1_nq9cdMxtdhQ0ZGL8OuSCUQ.jpeg",
          link: "vue-js",
        },
        {
          name: "Kelas Laravel",
          img: "http://phphostingindonesia.com/wp-content/uploads/2015/04/laravel.jpg",
          link: "laravel",
        },
      ],
    };
  },
};
</script>
