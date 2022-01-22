<template>
  <div>
    <h4>{{ message }}</h4>
    <h4>{{ nama }}</h4>
    <h4>{{ listNama }}</h4>
    <hr />
    <ol>
      <li v-for="(student, i) in listNama" :key="i">{{ student }}</li>
    </ol>
    <hr />
    <ol>
      <li v-for="(provinsi, i) in listProvinsi" :key="i">
        <ol>
          <li v-for="(city, j) in provinsi.cities" :key="j">{{ provinsi.name }} - {{ city.name }}</li>
        </ol>
      </li>
    </ol>
    <hr />
    {{ payload }}
    <div class="form-group">
      <label for="name">Nama Buku</label>
      <input type="text" v-model="payload.name" class="form-control" id="name" placeholder="Nama Buku" />
    </div>
    <div class="form-group">
      <label for="Kategori">Kategori</label>
      <select v-model="payload.type_book_id" class="form-control" id="kategori">
        <option value="1">Ensiklopedia</option>
        <option value="2">Novel</option>
        <option value="3">Pendidikan</option>
        <option value="4">Komik</option>
      </select>
    </div>
    <h3 v-if="payload.type_book_id == 1">Aku suka Ensiklopedia</h3>
    <h3 v-else-if="payload.type_book_id == 2">Aku gemar baca novel</h3>
    <h3 v-else-if="payload.type_book_id == 3">Aku suka buku pendidikan</h3>
    <h3 v-else-if="payload.type_book_id == 4">Aku mau jadi komikus</h3>
    <h3 v-else>Silahkan pilih kategori buku</h3>
    <hr />
    <h3 v-show="payload.type_book_id">Telah memilih kategori buku</h3>
    <Title :title="payload.name" />
    <Title title="Belajar Vue JS" />
    <hr />
    <div class="text-center">
      <h1 class="h1">{{ increment }}</h1>
      <button type="button" class="btn btn-primary" @click="tambahIncrement">Tambah</button>
    </div>
    <hr />
    <div class="text-center mt-5">
      <input type="text" class="form-control" v-model="todo" />
      <button type="button" class="btn btn-primary" @click="tambahTodo">Tambah</button>
      <div v-if="isNoTodolist">add todolist</div>
      <ul>
        <li v-for="(doing, i) in todolist" :key="i">{{ doing }}</li>
      </ul>
    </div>
    <div class="text-center mt-3">
      <input type="text" v-model="fullname" placeholder="fullname" class="form-control" />
      <div>Firstname : {{ firstname }}</div>
      <div>Lastname : {{ lastname }}</div>
      <div>Fullname : {{ fullname }}</div>
    </div>
    <div class="text-center mt-3">
      {{ payload2 }}
      <InputText name="Fullname" :val="payload2.fullname" @get="(newValue) => (this.payload2.fullname = newValue)" />
      <InputText name="Username" :val="payload2.username" @get="(newValue) => (this.payload2.username = newValue)" />
      <InputText
        name="Email"
        type="email"
        :val="payload2.email"
        @get="(newValue) => (this.payload2.email = newValue)"
      />
      <InputText name="Password" type="password" />
    </div>
    <Tutorial />
  </div>
</template>

<script>
export default {
  asyncData({ params }) {
    return {
      id: params.id,
      message: "Hello Vue.js!",
    };
  },
  data() {
    return {
      text: "",
      firstname: "Ghany",
      lastname: "Ersa",
      increment: 0,
      nama: "Ghany Abdillah Ersa",
      listNama: ["Fauzan", "Siska", "Yhido", "Nabil", "Aufa"],
      listProvinsi: [
        {
          id: 1,
          name: "DKI Jakarta",
          cities: [
            {
              id: 1,
              name: "Jakarta Selatan",
            },
            {
              id: 2,
              name: "Jakarta Barat",
            },
          ],
        },
        {
          id: 2,
          name: "Jawa Barat",
          cities: [
            {
              id: 1,
              name: "Bandung",
            },
            {
              id: 2,
              name: "Cirebon",
            },
          ],
        },
        {
          id: 3,
          name: "Jawa Tengah",
          cities: [
            {
              id: 1,
              name: "Semarang",
            },
            {
              id: 2,
              name: "Surakarta",
            },
          ],
        },
      ],
      payload: {
        name: "",
        type_book_id: "",
      },
      payload2: {
        fullname: "",
        username: "",
        email: "",
      },
      todo: "",

      todolist: [],
    };
  },
  computed: {
    fullname: {
      get() {
        return this.firstname + " " + this.lastname;
      },
      // GHANY ABDILLAH
      set(newValue) {
        // ["GHANY", "ABDILLAH", " "]
        const names = newValue.split(" ");
        this.firstname = names[0];
        this.lastname = names[names.length - 1];
      },
    },
    isNoTodolist() {
      return this.todolist.length == 0;
    },
    isMatch() {
      if (this.password == this.passwordConfirm) return "Password Cocok";
      else return "Password Tidak Cocok";
    },
  },
  methods: {
    tambahIncrement() {
      this.increment++;
    },
    tambahTodo() {
      this.todolist.push(this.todo);
      this.todo = "";
    },
  },
};
</script>
