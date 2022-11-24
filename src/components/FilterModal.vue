<template>
  <section class="popUpBase" v-if="showToken">
    <section class="popUpBase__container">
      <article class="popUpBase__container__title">
        <h3>{{ title }}</h3>
        <div @click="$emit('update:showToken', !showToken)">
          <img src="/src/assets/img/Close.svg" alt="" />
        </div>
      </article>

      <article class="popUpBase__container__form">
        <form>
          <div>
            <div class="modal">
              <article class="modal__grid">
                <select class="modal__grid--select">
                  <option
                    class="modal__grid--option"
                    value=""
                    @change="(e) => filter(e.target.value)"
                  >
                    Filter by
                  </option>
                  <option
                    class="modal__grid--option"
                    value="name"
                    @change="(e) => filter(e.target.value)"
                  >
                    Name
                  </option>
                  <option
                    class="modal__grid--option"
                    value="company"
                    @change="(e) => filter(e.target.value)"
                  >
                    Company
                  </option>
                  <option
                    class="modal__grid--option"
                    value="city"
                    @change="(e) => filter(e.target.value)"
                  >
                    City
                  </option>
                </select>
              </article>

              <div class="modal__grid">
                <select class="modal__grid--select">
                  <option
                    class="modal__grid--option"
                    value=""
                    @change="(e) => filter(e.target.value)"
                  >
                    Order by
                  </option>
                  <option
                    class="modal__grid--option"
                    value="name"
                    @change="(e) => filter(e.target.value)"
                  >
                    Name
                  </option>
                  <option
                    class="modal__grid--option"
                    value="username"
                    @change="(e) => filter(e.target.value)"
                  >
                    Username
                  </option>
                  <option class="modal__grid--option" value="city">City</option>
                </select>
                <select class="modal__grid--select">
                  <option
                    class="modal__grid--option"
                    value=""
                    @change="(e) => filter(e.target.value)"
                  >
                    Select an option
                  </option>
                  <option
                    class="modal__grid--option"
                    value="asc"
                    @change="(e) => filter(e.target.value)"
                  >
                    Ascending
                  </option>
                  <option
                    class="modal__grid--option"
                    value="desc"
                    @change="(e) => filter(e.target.value)"
                  >
                    Descending
                  </option>
                </select>
              </div>

              <article class="modal__btns">
                <button class="modal__btns--btn" value="reset" type="reset">
                  Delete filters
                </button>

                <button class="modal__btns--btn" type="button">
                  Apply filters
                </button>
              </article>
            </div>
          </div>
        </form>
      </article>
    </section>
  </section>
</template>

<script setup>
import apiFilter from "@/utils/filter";
import { ref } from "vue";

const users = apiFilter;

const filter = ref("");
const order = ref("");
const orderValue = ref("");

defineProps(
  {
    title: {
      type: String,
      default: "",
    },
    showToken: {
      type: Boolean,
      default: false,
    },
    showSucces: {
      type: Boolean,
      default: false,
    },
    action: {
      type: String,
      default: "",
    },
  },
  ["users"]
);
</script>

<style lang="scss">
.popUpBase {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 99;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  background-color: rgb(0, 6, 38, 0.8);
  &__container {
    width: 70%;
    padding: 3rem;
    background-color: white;
    border-radius: 1.6rem;
    overflow: hidden;
    @media (max-width: 700px) {
      padding: 1.5rem;
      width: 90%;
    }
    &__title {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding-bottom: 2rem;
      border-bottom: 1px solid #ebebeb;
      h3 {
        margin-bottom: 0;
        font-size: 3.6rem;
        font-weight: 600;
        color: #0d1520;
        margin-right: 2rem;
        @media (max-width: 700px) {
          font-size: 2.6rem;
        }
      }
      div {
        width: 4rem;
        height: 4rem;
        padding: 0.8rem;
        background-color: rgba(179, 191, 208, 0.3);
        border-radius: 100%;
        cursor: pointer;
      }
    }
    &__actions {
      display: flex;
      justify-content: end;
      padding-top: 2rem;
      button {
        margin-left: 1rem;
      }
    }
    &__form {
      padding-top: 2rem;
    }
  }
}

.modal {
  display: flex;
  flex-direction: column;
  gap: 2.4rem;
  &__grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 2.4rem;
    @media (max-width: 1000px) {
      grid-template-columns: 1fr;
    }
    &--select {
      padding: 1.2rem;
      border-radius: 0.8rem;
      border: none;
      background-color: rgba(179, 191, 208, 0.3);
      font-size: 1.8rem;
      outline: none;
    }
    &--option {
      font-size: 1.8rem;
    }
  }
  &__btns {
    display: flex;
    justify-content: flex-end;
    gap: 2.4rem;
    @media (max-width: 500px) {
      flex-direction: column;
    }
    &--btn {
      padding: 1.2rem 1.6rem;
      font-size: 1.6rem;
      background: $primary-color;
      border-radius: 1.6rem;
      color: #fff;
      border: none;
      cursor: pointer;
      &:hover {
        background: $tertiary-color;
      }
    }
  }
}
</style>