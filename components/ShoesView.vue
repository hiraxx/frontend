<template>
  <div>
    <button class="btn btn-success float-right" @click="onNew">
      New Shoe
    </button>
    <h5>Shoes View</h5>
    <hr>

    <form action="" @submit.prevent="">
          <b-form-group label="Name">
            <b-form-input v-model="shoe.name"></b-form-input>
          </b-form-group>
          <b-form-group label="Brand">
            <b-form-input v-model="shoe.brand"></b-form-input>
          </b-form-group>
          <b-form-group label="Size">
            <b-form-input type="number" v-model="shoe.size"></b-form-input>
          </b-form-group>
          <b-form-group label="Price">
            <b-form-input type="number" v-model="shoe.price"></b-form-input>
          </b-form-group>
          <b-form-group label="Date Acquired">
            <b-form-input type="date" v-model="shoe.acquired_on"></b-form-input>
          </b-form-group>
      <b-form-group>
        <button class="btn btn-primary" @click="onSave">Save Changes</button>
        <button class="btn btn-danger" @click="onDelete" v-if="shoe.id">Delete</button>
      </b-form-group>
    </form>
  </div>
</template>

<script>
export default {
  props: {
    shoe: {}
  },
  methods: {
    async onSave(){
      try {
        if(!this.shoe.id){
          await this.$axios.post('/api/shoes', this.shoe)
        }else{
          await this.$axios.put('/api/shoes/' + this.shoe.id, this.shoe)
        }

        this.$emit('save')
      }catch(err) {
        alert(err.response.data.message)
      }
    },
    onNew(){
      this.$emit('new')
    },
    async onDelete(){
      try{
        this.$axios.delete('/api/shoes/' + this.shoe.id)
        this.$emit('delete')
      }catch(err){
        alert(err.response.data.message)
      }
    }
  }
}
</script>

<style>

</style>