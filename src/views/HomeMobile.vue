<template>
  <div class="item_flex item_column_flex">
    <div class="fixed_position_only drop_mobile_navi">
      <SideNavigatorComponent />
    </div>
    <main>
      <MainMobileComponent />
    </main>
    <footer>
      <FooterMobileComponent />
    </footer>
  </div>
</template>
  
  <script>
import SideNavigatorComponent from "@/components/mobileNavigation/SideNavigatorComponent.vue";
import MainMobileComponent from "@/components/mobileMain/MainMobileComponent.vue";
import FooterMobileComponent from "@/components/mobileFooter/FooterMobileComponent.vue";
export default {
  name: "HomeMobile",
  components: {
    SideNavigatorComponent,
    MainMobileComponent,
    FooterMobileComponent,
  },
  props: {},
  data() {
    return {};
  },
  created() {},
  methods: {},
};
</script>