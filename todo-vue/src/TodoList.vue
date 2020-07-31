<template>
  <div class="list-wrapper">
    <h2>Your list:</h2>
    <transition-group name="fade" tag="ul" class="list">
      <li v-for="(item, index) in items" :key="`${item.label}-${index}`">
        <input :id="`item-${index}`" type="checkbox" @change="handleDone(index)" />
        <label
          :for="`item-${index}`"
          :class="{ crossed: item.done }"
        >
          {{ item.label }}
        </label>
      </li>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: {
    items: Array,
    handleDone: Function
  },
  data: () => ({
    item: ""
  }),
}
</script>

<style>
  .list {
    display: flex;
    flex-direction: column;
    max-height: 15rem;
    overflow: scroll;
  }

  .list li {
    margin-bottom: .5rem;
  }

  .crossed {
    text-decoration: line-through;
  }

  .list-wrapper {
    margin-top: 4rem;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }

  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }
</style>