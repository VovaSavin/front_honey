<template>
  <div class="bg_white width_calc_on_3">
    <div class="padding_bottom_1 pt-5">
      <h3>Зв'яжітся з нами</h3>
    </div>
    <div class="line_under_block margin_around"></div>
    <div class="item_flex item_column_flex item_content_around">
      <div>
        <div v-for="cont in contacts" :key="cont.id" class="item_column_flex">
          <div
            v-if="cont.our_address"
            class="item_column_flex font_times_new_roman"
          >
            <p>
              <img
                src="https://cdn-icons-png.flaticon.com/512/455/455705.png"
                alt="phone"
                width="20"
                height="20"
              />
              <span class="f_bold"> &nbsp;{{ cont.phone }}</span>
            </p>
            <div class="line_under_block margin_around"></div>
            <p>
              <img
                src="https://cdn-icons-png.flaticon.com/512/5076/5076545.png"
                alt="phone"
                width="20"
                height="20"
              />
              <span class="f_bold"> &nbsp;{{ cont.email }}</span>
            </p>
            <div class="line_under_block margin_around"></div>
            <p class="font_times_new_roman p-1">
              <img
                src="https://cdn-icons-png.flaticon.com/512/447/447031.png"
                alt="phone"
                width="20"
                height="20"
              />
              <span class="f_bold"> &nbsp;{{ cont.our_address }}</span>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
      
<script>
export default {
  name: "FooterContactComponent",
  props: {},
  data() {
    return {
      listContacts: null,
      contacts: null,
    };
  },
  created() {
    this.runGetData();
  },
  methods: {
    runGetData() {
      this.dataForContacts().then(() => this.getContactAndAddress());
    },
    async dataForContacts() {
      // Some data for contacts
      this.listContacts = [
        {
          value: 0,
          text: "Telegram",
        },
        {
          value: 1,
          text: "Viber",
        },
        {
          value: 2,
          text: "Facebook",
        },
      ];
    },
    async getContactAndAddress() {
      // Get data contacts
      this.contacts = await fetch(
        `${this.$store.getters.getServerUrl}/contacts/`
      )
        .then((response) => response.json())
        .catch(function (error) {
          console.log(error);
        });
    },
  },
};
</script>
      
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>