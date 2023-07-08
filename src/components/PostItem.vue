<template>
  <div class="post">
    <div>
      <div><strong>Название: </strong> {{ post.title }}</div>
      <div><strong>Описание: </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <custom-button type="error" @click="$emit('remove', post)"
        >Удалить</custom-button
      >
    </div>
  </div>
</template>

<script lang="ts">
import { IPost } from '@/types/Posts';
import { PropType, defineComponent } from 'vue';

export default defineComponent({
  components: {},
  props: {
    post: { type: Object as PropType<IPost>, required: true },
  },
});
</script>

<style lang="scss" scoped>
.post {
  padding: 15px;
  border: 2px solid $main-color;
  margin-top: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>
