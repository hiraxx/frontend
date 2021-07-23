<template>
  <div>
    <b-button v-b-modal.bookEntryModal variant="primary">Add Book</b-button>
    
    <b-modal id="bookEntryModal" title="Add Book" ok-title="Save Book" @ok="onAdd">
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
  data(){
    return {
      book: {}
    }
  },
  methods: {
    async onAdd(){
      this.$axios.post('/api/books', this.book)
      .then((res)=>{
        if(res.status==202){
          alert("Book Succesfully added")
          this.$emit('onAddEntry')
        }
      })
    }
  }
}
</script>

<style>

</style>