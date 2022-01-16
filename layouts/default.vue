<template>
  <div id="app">
    <div class="main-wrapper">
      <PartialsNavbar />
      <PartialsSidebar />
      <div class="main-content">
        <section class="section">
          <div class="section-header">
            <h1>Blank Page</h1>
          </div>
          <div class="section-body">
            <Nuxt />
          </div>
        </section>
      </div>
      <PartialsFooter />
    </div>
  </div>
</template>