<template>
  <div class="item_flex item_content_between">
    <div class="item_flex_inline width_50_percent text_left">
      <div class="margin_rr">
        <img src="../assets/img10.png" alt="logo" width="100" height="90" />
      </div>
      <div class="item_flex item_column_reverse_flex padding_bottom_04">
        <em class="opacity_05 font_14"> послуги </em>
        <b class="font_times_new_roman font_18">Медові</b>
      </div>
    </div>
    <div class="width_50_percent">
      <ul class="item_flex item_content_between case_up none_decoration">
        <li v-for="navi in navigation" :key="navi.value">
          <a
            class="none_decoration black_color f_family_abril"
            :href="navi.link"
          >
            {{ navi.text }}
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>
  
<script>
export default {
  name: "HeaderComponent",
  props: {},
  data() {
    return {
      navigation: JSON.parse(localStorage.getItem("navigation")),
    };
  },
  created() {},
};
</script>
  
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
  