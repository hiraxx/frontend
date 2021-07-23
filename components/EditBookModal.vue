<template>
  <div>    
    <b-modal id="editBookModal" title="Edit Book" ok-title="Save Book" @ok="onEdit">
      <form action="#">
        <b-form-group
         label="Title" 
         label-for="title">
          <b-form-input id="title" v-model="book.title" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Author" 
         label-for="author">
          <b-form-input id="author" v-model="book.author" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Description" 
         label-for="description">
          <b-form-input id="description" v-model="book.description" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Book No" 
         label-for="book No">
          <b-form-input id="book No" type="number" v-model="book.book_no" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Date Published" 
         label-for="published_on">
          <b-form-input id="published_on" type="date" v-model="book.date_published" trim></b-form-input>
        </b-form-group>
        <b-form-group
         label="Date Acquired" 
         label-for="acquired_on">
          <b-form-input id="acquired_on" type="date" v-model="book.acquired_on" trim></b-form-input>
        </b-form-group>
      </form>
    </b-modal>  
  </div>
</template>

<script>
export default {
  props: {
    book: {}
  },
  methods: {
    async onEdit(){
      this.$axios.put('/api/books/' + this.book.id, this.book)
      .then((res)=>{
        if(res.status==202){
          alert("Book Succesfully Edited")
        }
      })
      .catch((err)=>{
        alert(err.message)
      })
    }
  }
}
</script>

<style>

</style>