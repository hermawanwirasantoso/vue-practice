<template>
  <div>
    <nav >
      <div class="nav-wrapper green">
        <form>
          <div class="input-field">
            <input id="search" type="search" v-on:input="$emit('input',($event.target.value))" required>
            <label class="label-icon" for="search"><i class="material-icons">search</i></label>
            <i class="material-icons">close</i>
          </div>
        </form>
      </div>
    </nav>
  </div>
</template>


<script>
export default {};
</script>
<style>
</style>
