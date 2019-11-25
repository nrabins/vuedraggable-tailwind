<template>
  <li class="p-4 mb-3 flex justify-between items-center bg-white shadow rounded-lg cursor-move">
    <div class="flex items-center">
      <img :src="user.avatar" :alt="user.name" class="w-10 h-10 rounded-full" />
      <p class="ml-2 text-gray-700 font-semibold font-sans tracking-wide">{{user.name}}</p>
    </div>
    <div class="flex">
      <button
        aria-label="Edit user"
        class="p-1 focus:outline-none focus:shadow-outline text-teal-500 hover:text-teal-600"
        @click="$emit('edit', user)"
      >
        <EditIcon />
      </button>
      <button
        aria-label="Delete user"
        class="p-1 focus:outline-none focus:shadow-outline text-red-500 hover:text-red-600"
        @click="$emit('delete', user)"
      >
        <Trash2Icon />
      </button>
    </div>
  </li>
</template>

<script>
import { EditIcon, Trash2Icon } from "vue-feather-icons";

export default {
  components: {
    EditIcon,
    Trash2Icon
  },
  props: {
    user: {
      type: Object,
      default: () => ({})
    }
  }
};
</script>

<style>
</style>