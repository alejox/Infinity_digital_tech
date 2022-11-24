<template>
  <section class="user">
    <section class="user__card">
      <article class="user__header">
        <img class="user__header--img" src="@/assets/img/team.png" alt="" />
        <h1 class="user__header--title">Users List</h1>
        <button @click="showPopUp = true" class="user__header--button">
          Filters
        </button>
      </article>
    </section>

    <section class="user__card user__card--white">
      <article class="user__main">
        <Users :users="users" />
      </article>
    </section>
  </section>
  <FilterModal
    v-model:showToken="showPopUp"
    title="Select a filter"
    :users="users"
  >
  </FilterModal>
</template>

<script>
import Users from "@/components/Users.vue";
import FilterModal from "@/components/FilterModal.vue";
// import apiFilter from "@/utils/filter";
import axios from "axios";
import { ref } from "vue";

const showPopUp = ref(false);

const users = ref([]);

const getData = async () => {
  try {
    const { data } = await axios.get(
      "https://jsonplaceholder.typicode.com/users"
    );
    users.value = data;
  } catch (error) {
    console.log(error);
  }
};

getData();

export default {
  components: {
    Users,
    FilterModal,
  },
  data() {
    return {
      showPopUp: false,
      users,
    };
  },
};
</script>

<style lang="scss" scoped>
.user {
  &__card {
    background-color: $primary-color;
    padding: 2.4rem;
    border-radius: 1.6rem;
    &--white {
      background: $secondary-color;
      border: $border;
    }
  }
  display: flex;
  flex-direction: column;
  gap: 2.4rem;
  margin: 2rem;
  &__header {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2.4rem;
    &--img {
      width: 20rem;
      display: block;
    }
    &--title {
      font-size: 4rem;
      font-weight: 700;
      line-height: 4.8rem;
      text-align: center;
      color: $secondary-color;
    }
    &--button {
      padding: 1.6rem;
      border-radius: 1.6rem;
      font-size: 1.4rem;
      font-weight: 600;
      width: 20rem;
      cursor: pointer;
      transition: all 0.1s ease;
      &:hover {
        background: $tertiary-color;
        color: $secondary-color;
      }
    }
  }
}
</style>