<template>
  <main class="c-main">
    <div class="container-fluid">
      <div class="fade-in">
        <div class="row">
          <div class="col-md-12">
            <div class="card border-0 rounded shadow-sm border-top-orange">
              <div class="card-header">
                <span class="font-weight-bold"
                  ><i class="fa fa-laptop"></i> SLIDERS</span
                >
              </div>
              <div class="card-body">
                <nuxt-link
                  :to="{ name: 'admin-sliders-create' }"
                  class="btn btn-warning btn-sm mb-3 p-2"
                >
                  <i class="fa fa-plus-circle"></i> ADD NEW</nuxt-link
                >
                <b-table
                  striped
                  bordered
                  hover
                  :items="sliders.data"
                  :fields="fields"
                  show-empty
                >
                  <template v-slot:cell(image)="data">
                    <img class="img-fluid" width="200" :src="data.item.image" />
                  </template>
                </b-table>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
<script>
export default {
  //layout
  layout: "admin",

  //meta
  head() {
    return {
      title: "Sliders - Administrator",
    };
  },

  //data function
  data() {
    return {
      //table header
      fields: [
        {
          label: "Image",
          key: "image",
          tdClass: "text-center",
        },
        {
          label: "Link Slider",
          key: "link",
        },
        {},
      ],
    };
  },
  //hook "asyncData"
  async asyncData({ store }) {
    await store.dispatch("admin/slider/getSlidersData");
  },
  label: "Actions",
  key: "actions",
  tdClass: "text-center",

  //computed
  computed: {
    //sliders
    sliders() {
      return this.$store.state.admin.slider.sliders;
    },
  },
};
</script>
<style></style>
