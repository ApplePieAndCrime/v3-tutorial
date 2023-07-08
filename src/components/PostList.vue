<template>
  <div v-if="posts.length > 0">
    <h3>Список</h3>
    <post-item
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @remove="$emit('remove', post)"
    />
  </div>
  <h2 v-else style="color: red">Список постов пуст</h2>
</template>

<script lang="ts">
import { PropType, defineComponent } from 'vue';
import { IPost } from '@/types/Posts';
import PostItem from '@/components/PostItem.vue';

export default defineComponent({
  components: { PostItem },
  props: {
    posts: {
      type: Array as PropType<IPost[]>,
      required: true,
    },
  },
  data() {
    return {};
  },
  methods: {},
});
</script>

<style lang="scss" scoped></style>
