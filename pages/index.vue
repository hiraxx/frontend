<template>
  <div>
    <NavBar />
    <div class="container mt-5">
      <h1 class="text-center">
        <span>Welcome</span>
        <span v-if="$auth.loggedIn">
          {{$auth.user.name}}
        </span>
      </h1>
    </div> 
  </div>
</template>

<script>
export default {
  auth: false
}
</script>

<style>
</style>