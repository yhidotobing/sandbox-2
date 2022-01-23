<template>
  <div>
    <InputButton> Tambah </InputButton>
    <InputButton> <h2>Hello World</h2> </InputButton>
    <BootstrapCard>
      <p>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Similique, reprehenderit! Quas veniam accusantium
        asperiores error aperiam tenetur ipsa commodi hic eaque necessitatibus mollitia, sint, perferendis, dicta optio
        fugit sequi nostrum?
      </p>
    </BootstrapCard>
    <br />
    <BootstrapCard>
      <template v-slot:header>
        <img src="~/assets/img/unsplash/pegunungan.jpg" style="height: 100px" alt="" />
      </template>

      <template v-slot:default>
        <p>Body CARD</p>
      </template>

      <template v-slot:footer>
        <InputButton> Tambah </InputButton>
      </template>
    </BootstrapCard>
  </div>
</template>
