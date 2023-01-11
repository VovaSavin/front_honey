<template>
  <div
    class="
      position_rel_form
      w-25
      margin_l_3
      form_oder_bg
      b_radius_3
      f_family_arial
    "
  >
    <form
      @submit="sendOrder"
      class="item_flex item_column_flex margin_around_06"
      action="#"
    >
      <div class="item_flex item_vertical_base">
        <span class="font_14">+380 &nbsp;</span>
        <input
          class="font_14 w-100"
          type="tel"
          name="tele"
          id="e_mail"
          maxlength="10"
          cols="40"
          placeholder="Ваш номер телефону..."
          v-model="order.phone_user"
          required="true"
        />
      </div>
      <span class="font_10 margin_around_02">
        Вкажіть номер телефону для оформлення цього замовлення
      </span>
      <textarea
        name="comment"
        id="comment"
        cols="5"
        rows="3"
        class=""
        placeholder="Коментар до замовлення..."
        v-model="order.comment"
      ></textarea>
      <span class="font_10 margin_around_02">
        Коментар для цього замовлення
      </span>
      <input
        @click="sendOrder"
        class="margin_around font_14"
        type="submit"
        value="Відправити"
      />
    </form>
    <div></div>
  </div>
</template>
    
<script>
import modalComponent from "@/components/modal/modalComponent.vue";

import axios from "axios";
export default {
  name: "orderFormComponent",
  props: {
    goodName: String,
  },
  components: {
    modalComponent,
  },
  data() {
    return {
      newShowModal: false,
      order: {
        name_order: this.goodName,
        phone_user: null,
        individual_key: "a326c4b3-5099-4c88-8569-5eebc5ea8091",
        comment: null,
      },
    };
  },
  created() {},
  methods: {
    showModalOrder() {
      this.newShowModal = true;
    },
    async sendOrder(e) {
      // Forming JSON for send letter to mail
      if (this.order.phone_user != null) {
        confirm(
          `Підтвердження замовлення: \n ${this.order.name_order}\n ${this.order.phone_user} \n ${this.order.comment}`
        );
        e.preventDefault();
        await axios({
          url: `${this.$store.getters.getServerUrl}/orders_all/`,
          method: "post",
          headers: {
            accept: "application/json",
            "Content-Type": "application/json",
          },
          data: JSON.stringify(this.order),
        })
          .then(function (response) {
            console.log(response);
            alert("Замовлення відправлено!");
            location.reload();
          })
          .catch(function (error) {
            console.log(error);
          });
      } else {
        alert("Введіть номер телефону!");
      }
    },
  },
};
</script>
    
<style scoped>
</style>
