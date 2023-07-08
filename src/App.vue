<template>
  <div class="app">
    <h1>Страница с постами</h1>

    <custom-button @click="showDialog" type="success" style="margin: 15px"
      >Создать пост</custom-button
    >
    <custom-dialog v-model:show="dialogVisible">
      <post-form @create="createPost" />
    </custom-dialog>
    <post-list :posts="posts" @remove="removePost" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios';
import PostForm from '@/components/PostForm.vue';
import PostList from '@/components/PostList.vue';
import { IPost } from './types/Posts';

export default defineComponent({
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [] as Array<IPost>,
      dialogVisible: false,
      modificatorValue: '',
    };
  },
  methods: {
    createPost(post: IPost) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post: IPost) {
      this.posts.splice(
        this.posts.findIndex(item => item.id === post.id),
        1
      );
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        const res = await axios.get(
          'https://jsonplaceholder.typicode.com/posts',
          { params: { _limit: 10 } }
        );
        console.log({ res });
        this.posts = res.data;
      } catch (err) {
        console.error('fetchPosts error: ', err);
      }
    },
  },
});
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>
