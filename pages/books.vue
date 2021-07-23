<template>
  <div>
    <NavBar/>
    <div class="container mt-5">
      <h1>My Books</h1>
      <div class="row">
        <div class="col-6">
          <h5>List of Books</h5>

        </div>
        <div class="col-6">
          <BooksView/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return {
      books: [],
      selectedBook: {}
    }
  },
  methods: {
    async getAll(){
      await this.$axios.get('/api/books')
      .then((res)=>{
        if(res.status==200){
          this.books = res.data
        }
      })
    },
    onEdit(selectedBook){
      this.selectedBook = selectedBook
      this.$bvModal.show('editBookModal')
    },
    onDelete(selectedBook){
      this.selectedBook = selectedBook
      this.$bvModal.show('deleteBookModal')
    }
  },
  created(){
    this.getAll()  
  }
}
</script>

<style>

</style>