<template>
<div class="container mt-3">
       <div class="row">
              <div class="col">
                     <p class="h3 text-success fw-bold">
                            Contact Manager
                     <router-link to="/contacts/add" class="btn btn-success btn-sm"><i class="fa fa-plus-circle"></i> New</router-link>
                     </p>
                     <p class="fst-italic">Lorem ipsum dolor sit amet consectetur adipisicing elit. Possimus totam molestias ipsa blanditiis voluptatibus adipisci omnis optio, asperiores, ab ipsam dicta dolor aspernatur ea. Sequi expedita iure saepe tenetur enim.</p>
                     <form>
                            <div class="row">
                                   <div class="col-md-6">
                                          <div class="row">
                                          <div class="col">
                                   <input type="text" class="form-control" placeholder="Search Name">
                            </div>
                            <div class="col">
                                   <input type="submit" class="btn btn-outline-dark">
                            </div>
                            </div>
                                   </div>
                            </div>
                     </form>
              </div>
       </div>
</div>
</template>

<script>
export default{
       name : 'ContactManager'
}
</script>

<style scoped>
</style>
