<template>
  <section class="container mt-5">
    <div class="row">
      <div class="col-4 offset-4">
        <div>
          <input
            v-model="name"
            type="text"
            class="form-control"
            placeholder="What's your name?"
            @input="onNameInput"
          />
        </div>
        <h2 class="text-center mt-2">
          {{ greeting }}
        </h2>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      greeting: '',
    }
  },

  methods: {
    onNameInput() {
      this.$axios.$get(`/api/hello/${this.name}`).then((response) => {
        this.greeting = response.message
      })
    },
  },
}
</script>
