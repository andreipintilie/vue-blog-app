<template>
  <div>
    <div v-for="(post, index) in posts" v-bind:key="index">
      <div v-if="post.title.length > 0">
        <b-card no-body class="my-5">
          <b-card-header>
            <b-card-text>
              {{ post.title }}
              <b-icon-trash-fill
                id="removeBtn"
                title="Remove post"
                class="float-right my-1"
                @click="removePost(index)"
              ></b-icon-trash-fill>
            </b-card-text>
          </b-card-header>
          <b-card-body>
            <b-card-text id="content">{{ post.content }}</b-card-text>
            <small>Tags:</small>
            <small
              id="tag"
              v-for="(tag,index) in post.tags"
              :key="index"
              class="text-muted"
            >#{{ tag }}</small>
          </b-card-body>
          <b-card-footer>
            <b-card-text class="text-muted">Category: {{ post.category }}</b-card-text>
          </b-card-footer>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Posts",
  props: ["posts"],
  methods: {
    removePost: function(index) {
      this.$emit("remove-post", index);
    }
  }
};
</script>

<style scoped>
#content {
  white-space: pre-line;
}
#removeBtn {
  color: #333333;
  cursor: pointer;
  transition: all 0.4s ease-in-out;
}
#removeBtn:hover {
  color: #666666;
}
#removeBtn:active {
  color: #141414;
}
#tag {
  margin-left: 10px;
  transition: all 0.4s ease-in-out;
}
#tag:hover {
  color: black !important;
  cursor: pointer;
}
</style>