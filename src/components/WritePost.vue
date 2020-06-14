<template>
  <div>
    <b-card no-body class="my-5">
      <b-card-header>
        <b-card-text>Write a post</b-card-text>
      </b-card-header>
      <b-card-body>
        <label>Title</label>
        <input type="text" v-model="titleModel" />
        <label class="my-1">Category</label>
        <b-form-select v-model="categoryModel" :options="options" size="sm"></b-form-select>
        <label class="my-1">Content</label>
        <textarea cols="30" rows="5" v-model="contentModel"></textarea>
        <label>Tags</label>
        <b-form-tags input-id="tags-basic" v-model="tagModel"></b-form-tags>
        <b-button class="my-4" @click="submitPost">Publish</b-button>
      </b-card-body>
    </b-card>
  </div>
</template>

<script>
export default {
  name: "WritePost",
  data() {
    return {
      titleModel: "",
      contentModel: "",
      categoryModel: null,
      tagModel: [],
      options: [
        { value: null, text: "Please select a category" },
        { value: "News", text: "News" },
        { value: "Lifestyle & Health", text: "Lifestyle & Health" },
        { value: "Music", text: "Music" },
        { value: "IT&C", text: "IT&C" }
      ]
    };
  },
  methods: {
    submitPost: function() {
      if (
        this.titleModel.length <= 3 ||
        this.contentModel.length <= 5 ||
        this.categoryModel === null ||
        this.tagModel.length == 0
      )
        return;

      this.$emit(
        "add-post",
        this.titleModel,
        this.contentModel,
        this.categoryModel,
        this.tagModel
      );
      this.titleModel = "";
      this.contentModel = "";
      this.categoryModel = null;
      this.tagModel = [];
    }
  }
};
</script>

<style scoped>
input[type="text"],
textarea {
  width: 100%;
  border: none;
  border: 1px solid rgba(0, 0, 0, 0.3);
  border-radius: 5px;
  line-height: 1rem;
  padding: 5px;
}
.btn {
  background-color: #39536b;
}
.btn:hover {
  background-color: #456583;
}
.btn:active {
  background-color: #2f455a !important; /* I used !important to overwrite the bootstrap rule */
}
label {
  padding: 10px 0px;
}
</style>