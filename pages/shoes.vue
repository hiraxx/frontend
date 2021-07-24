<template>
  <div>
    <NavBar/>
    <div class="container">
      <h1 >Shoes</h1>
      <div class="row">
        <div class="col-6">
          <h5>List of Shoes</h5>
          <ul class="list-group">
            <li class="list-group-item list-group-item-action" v-for="shoe in shoes" :key="shoe.id" @click="onSelected(shoe)">
              {{shoe.name}} <span class="float-right">{{shoe.price}}</span>
            </li>
          </ul>
        </div>
        <div class="col-4">
          <ShoesView :shoe="selectedShoe" @new="onNewShoes" @save="onChanges" @delete="onChanges"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      shoes: [],
      selectedShoe: {}
    }
  },
  methods: {
    async getShoes(){
      await this.$axios.get('/api/shoes')
      .then((res)=>{
        if(res.status==200){
          this.shoes = res.data
        }
      })
    },
    onChanges(){
      this.getShoes()
      this.selectedShoe = {}
    },
    onNewShoes(){
      this.selectedShoe = {}
    },
    onSelected(shoe){
      this.selectedShoe = shoe 
    }
  },
  created() {
    this.getShoes()
  }
}
</script>

<style>

</style>