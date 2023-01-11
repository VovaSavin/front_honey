<template>
  <div
    id="inf-main"
    class="item_flex item_content_around margin_t_3 margin_b_3"
  >
    <div class="margin_t_3 item_flex item_column_flex max_width_75">
      <div
        class="
          item_flex_inline item_vertical_base item_content_center
          f_family_abril
        "
      >
        <h2 class="case_up">Чому ми</h2>
        <h2>?</h2>
      </div>
      <div class="item_flex item_content_between text_left">
        <div class="f_family_abril font_18">
          {{ info }}
        </div>
      </div>
    </div>
    <div>
      <img src="../../assets/img6.png" alt="mainImg" width="540" height="369" />
    </div>
  </div>
</template>
      
<script>
export default {
  name: "MainInfoComponent",
  props: {},
  data() {
    return {
      info: JSON.parse(localStorage.getItem("about"))[0].description,
    };
  },
  created() {},
  methods: {},
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>