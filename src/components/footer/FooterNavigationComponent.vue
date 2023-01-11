<template>
  <div class="bg_black_b item_column_flex width_calc_on_3 pt-5">
    <div class="padding_bottom_1 f_color_white">
      <h3>Навіцація</h3>
    </div>
    <div class="line_under_block margin_around"></div>
    <div class="">
      <ul
        class="
          item_flex item_column_flex item_content_between
          case_up
          none_decoration
          padding_0
        "
      >
        <li class="" v-for="navi in navigation" :key="navi.value">
          <a
            class="none_decoration f_color_white f_family_abril"
            :href="navi.link"
          >
            {{ navi.text }}
          </a>
          <div
            v-if="navi.value != 3"
            class="line_under_block margin_around"
          ></div>
        </li>
      </ul>
    </div>
  </div>
</template>
      
<script>
export default {
  name: "FooterNavigationComponent",
  props: {},
  data() {
    return {
      navigation: JSON.parse(localStorage.getItem("navigation")),
    };
  },
  created() {},
  methods: {},
};
</script>
      
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>