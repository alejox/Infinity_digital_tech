<template>
  <section class="users">
    <article class="users__table__container">
      <article class="users__table__table">
        <article class="users__table__table-header">
          <p>Name</p>
          <p>Website</p>
          <p>Company</p>
          <p>City</p>
        </article>
        <article v-for="user in users" class="users__table__table-row">
          <p>{{ user.name }}</p>
          <p>{{ user.website }}</p>
          <p>{{ user.company.name }}</p>
          <p>{{ user.address.city }}</p>
        </article>
      </article>
    </article>
  </section>
</template>

<script setup>

defineProps(["users"]);

</script>

<style lang="scss" scoped>
.users {
  &__table {
    &__container {
      overflow: hidden;
    }
    &__title {
      display: flex;
      justify-content: space-between;
      input {
        max-width: 300px;
      }
    }
    @include Table(3);
  }
}
</style>


