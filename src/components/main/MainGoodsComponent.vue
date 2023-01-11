<template>
  <div
    id="goods"
    class="item_flex item_column_flex font_times_new_roman padding_around"
  >
    <div class="item_flex">
      <div
        id="carouselExampleControls"
        class="
          item_flex item_content_between
          carousel
          slide
          w-100
          margin_b_3 margin_t_3
        "
        data-bs-ride="carousel"
      >
        <div class="carousel-inner">
          <div v-for="good in goods" :key="good.id">
            <div v-if="good.if_show">
              <div
                class="carousel-item"
                :class="{
                  active: good.id == goods[0].id,
                  '': good.id != goods[0].id,
                }"
              >
                <div class="item_flex item_content_around padding_around">
                  <div class="">
                    <img
                      :src="good.image"
                      class="services__image max_width_5 m_height_5 b_radius_3"
                      :alt="good.name_good"
                      width="355"
                      height="255"
                    />
                  </div>
                  <div class="goods_visibility w-50">
                    <h3 class="">
                      {{ good.name_good }}
                    </h3>
                    <p
                      class="
                        f_bold
                        font_18
                        text_al_justify
                        padding_around padding_r_3 padding_l_3
                      "
                    >
                      {{ good.description }}
                    </p>
                    <section class="pb-3 prices">
                      <div class="my-container">
                        <div class="row m-0">
                          <div
                            class="item_flex item_content_center prices-table"
                          >
                            <table>
                              <tbody>
                                <tr>
                                  <td>
                                    Від <b>{{ good.price_from }}</b> грн
                                  </td>
                                </tr>
                              </tbody>
                            </table>
                          </div>
                        </div>
                      </div>
                    </section>
                    <div
                      v-if="showOrderForm"
                      class="
                        item_flex
                        item_column_flex
                        item_content_around
                        item_vertical_base
                      "
                    >
                      <div class="position_rel_form_close w-50 margin_l_3 mb-1">
                        <svg
                          id="close_btn"
                          xmlns="http://www.w3.org/2000/svg"
                          width="28"
                          height="28"
                          fill="black"
                          class="
                            bi bi-x-lg
                            cursor_point
                            border_sq
                            cls_btn_cross
                          "
                          viewBox="0 0 16 16"
                          @click="closekBtnToOrder()"
                        >
                          <path
                            fill-rule="evenodd"
                            d="M13.854 2.146a.5.5 0 0 1 0 .708l-11 11a.5.5 0 0 1-.708-.708l11-11a.5.5 0 0 1 .708 0Z"
                          />
                          <path
                            fill-rule="evenodd"
                            d="M2.146 2.146a.5.5 0 0 0 0 .708l11 11a.5.5 0 0 0 .708-.708l-11-11a.5.5 0 0 0-.708 0Z"
                          />
                        </svg>
                      </div>
                      <orderFormComponent :goodName="good.name_good" />
                    </div>
                    <div>
                      <input
                        v-if="!showOrderForm"
                        @click="clickBtnToOrder()"
                        class="
                          btn
                          margin_around
                          cls_btn_cross
                          f_family_arial
                          font_14
                        "
                        type="submit"
                        value="Замовити"
                      />
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <button
          class="carousel-control-prev"
          type="button"
          data-bs-target="#carouselExampleControls"
          data-bs-slide="prev"
        >
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Previous</span>
        </button>
        <button
          class="carousel-control-next"
          type="button"
          data-bs-target="#carouselExampleControls"
          data-bs-slide="next"
        >
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Next</span>
        </button>
      </div>
    </div>
  </div>
</template>
      
<script>
import orderFormComponent from "@/components/forms/orderFormComponent.vue";
export default {
  name: "MainGoodsComponent",
  components: {
    orderFormComponent,
  },
  props: {},
  data() {
    return {
      goods: JSON.parse(localStorage.getItem("goods")),
      showOrderForm: false,
    };
  },
  created() {},
  methods: {
    clickBtnToOrder() {
      this.showOrderForm = true;
      document.querySelector("#app").classList.add("bg_tr_black");
    },
    closekBtnToOrder() {
      this.showOrderForm = false;
      document.querySelector("#app").classList.remove("bg_tr_black");
    },
    getNameOrder(nameInStorage, parametr) {
      // Set data in to local storage
      localStorage.setItem(nameInStorage, JSON.stringify(parametr));
    },
  },
};
</script>
      
      <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.goods_visibility {
  opacity: 1;
}
/* .goods_visibility:hover {
  opacity: 1;
} */
.services__image::before {
  content: "";
  position: absolute;
  background: rgba(0, 0, 0, 0.5);
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
}
.d-line-wrap {
  display: flex;
  flex-direction: column-reverse;
}
.services__button {
  position: absolute;
  left: 12.5%;
  top: 16%;
  width: 75%;
  height: 70%;
  opacity: 0;
  z-index: 10;
  background: transparent;
  -webkit-transition: all 0.3s ease-out;
  -o-transition: all 0.3s ease-out;
  transition: all 0.3s ease-out;
}
.services__button:hover {
  opacity: 1;
  background: rgba(70, 70, 70, 0.596);
}
.align-center {
  -webkit-box-pack: center;
  -ms-flex-pack: center;
  justify-content: center;
}
.d-flex {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
  -ms-flex-flow: row wrap;
  flex-flow: row wrap;
  align-items: center;
}
button:hover {
  background-color: rgba(128, 128, 128, 0.459);
}
</style>