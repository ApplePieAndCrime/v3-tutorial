<template>
  <form action="" @submit.prevent>
    <h3>Создание поста</h3>
    <custom-input
      v-model:value="post.title"
      v-model:myvalue="post.title"
      type="text"
      placeholder="Название"
    />
    <custom-input
      v-model:value="post.body"
      type="text"
      placeholder="Описание"
    />
    <custom-button
      @click="createPost"
      type="success"
      style="align-self: flex-end; margin-top: 15px"
      >Создать</custom-button
    >
  </form>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  components: {},
  data() {
    return {
      post: {
        id: 0,
        title: '',
        body: '',
      },
    };
  },
  methods: {
    createPost() {
      this.post.id = new Date().getTime();
      this.$emit('create', this.post);
      this.post = {
        id: 0,
        title: '',
        body: '',
      };
    },
  },
});
</script>

<style lang="scss" scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
