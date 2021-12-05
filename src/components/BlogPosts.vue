<template>
  <li>
      <div v-if="!edit">
        <h2>{{title}}</h2>
        <div>{{body}}</div>
        <button @click="Edit">Edit</button>
      </div>
      <div v-if="edit">
          <input type="text" v-model="title">
          <input type="text" v-model="body">
          <button @click="Save">Save</button>
      </div>
  </li>
</template>

<script>
export default {
    props: ['post'],
    data() {
        return {
            
            title: this.post.title,
            body: this.post.body,
            edit: false,
        }
    },
    methods: {
        Edit() {
            this.edit = true
        },
        Save() {
            this.edit = false
            this.$emit('post-item-changed', {
                original: this.post,
                new: {
                    title: this.title,
                    body: this.body
                    },
            })
        }
    }
}
</script>