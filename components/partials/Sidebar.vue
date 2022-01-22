<template>
  <!-- sidebar -->
  <div class="main-sidebar">
    <aside id="sidebar-wrapper">
      <div class="sidebar-brand">
        <a href="index.html">Stisla</a>
      </div>
      <div class="sidebar-brand sidebar-brand-sm">
        <a href="index.html">St</a>
      </div>
      <ul class="sidebar-menu">
        <li v-for="(sidebar, i) in listMenu" :key="i">
          <a class="nav-link" href="blank.html"
            ><i class="far fa-square"></i> <span>{{ sidebar }}</span></a
          >
        </li>
      </ul>

      <div class="mt-4 mb-4 p-3 hide-sidebar-mini">
        <a href="https://getstisla.com/docs" class="btn btn-primary btn-lg btn-block btn-icon-split">
          <i class="fas fa-rocket"></i> Documentation
        </a>
      </div>
    </aside>
  </div>
  <!-- sidebar -->
</template>
<script>
export default {
  data() {
    return {
      listMenu: ["Dashboard", "Our Class", "My Class", "Presence"],
    };
  },
};
</script>
