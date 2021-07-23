<template>
   <div>    
    <b-modal id="deleteBookModal" title="Delete Book" ok-title="Delete Book" @ok="onDelete">
      Are you sure you want to continue? <br>
      {{book.title}} - {{book.author}}
    </b-modal>  
  </div>
</template>

<script>
export default {
  props: {
    book: {}
  },
  methods: {
    async onDelete(){
      this.$axios.delete('/api/books/' + this.book.id)
      .then((res)=>{
        if(res.status==202){
          alert("Book Succesfully Deleted")
          this.$emit('onDeleteEntry')
        }
      })
    }
  }
}
</script>

<style>

</style>
