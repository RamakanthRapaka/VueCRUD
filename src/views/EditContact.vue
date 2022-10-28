<template>
  <div class="container mt-3">
    <div class="row">
      <div class="col">
        <p class="h3 text-success fw-bold">Edit Contact</p>
        <p class="fst-italic">
          Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolores sit
          ex molestiae nisi unde, iure voluptatum nihil, saepe deserunt ad ipsum
          impedit id quisquam animi, porro qui eligendi aliquam dolore!
        </p>
      </div>
    </div>
  </div>
  <div class="container mt-3">
    <div class="row">
      <div class="col-md-4">
        <form @submit.prevent="updateSubmit()">
          <div class="mb-2">
            <input required
              v-model="contact.name"
              type="text"
              class="form-control"
              placeholder="Name"
            />
          </div>
          <div class="mb-2">
            <input required
              v-model="contact.photo"
              type="text"
              class="form-control"
              placeholder="Photo URL"
            />
          </div>
          <div class="mb-2">
            <input required
              v-model="contact.email"
              type="text"
              class="form-control"
              placeholder="Email"
            />
          </div>
          <div class="mb-2">
            <input required
              v-model="contact.mobile"
              type="text"
              class="form-control"
              placeholder="Mobile"
            />
          </div>
          <div class="mb-2">
            <input required
              v-model="contact.company"
              type="text"
              class="form-control"
              placeholder="Company"
            />
          </div>
          <div class="mb-2">
            <input required
              v-model="contact.title"
              type="text"
              class="form-control"
              placeholder="Title"
            />
          </div>
          <div class="mb-2">
            <select required
              v-model="contact.groupId"
              v-if="groups.length > 0"
              class="form-control"
            >
              <option value="">Select Group</option>
              <option :value="group.id" v-for="group of groups" :key="group.id">
                {{ group.name }}
              </option>
            </select>
          </div>
          <div class="mb-2">
            <input type="submit" class="btn btn-success" value="Update" />
          </div>
        </form>
      </div>
      <div class="col-md-4">
        <img
          src="https://cdn-icons-png.flaticon.com/512/219/219986.png"
          alt=""
          class="contact-img"
        />
      </div>
    </div>
  </div>
</template>
    
    <script>
import { ContactService } from "@/services/ContactService";
export default {
  name: "EditContact",
  data: function () {
    return {
      contactId: this.$route.params.contactId,
      loading: false,
      contact: {
        name: "",
        email: "",
        photo: "",
        mobile: "",
        company: "",
        title: "",
        groupId: "",
      },
      errorMessage: null,
      groups: [],
    };
  },
  created: async function () {
    try {
      this.loading = true;
      let response = await ContactService.getContact(this.contactId);
      let groupResponse = await ContactService.getAllGroups();
      this.contact = response.data;
      this.groups = groupResponse.data;
      this.loading = false;
    } catch (error) {
      this.errorMessage = error;
      this.loading = false;
      console.log(error);
    }
  },
  methods: {
    updateSubmit: async function () {
      try {
        let response = await ContactService.updateContact(
          this.contact,
          this.contactId
        );
        if (response) {
          return this.$router.push("/");
        } else {
          return this.$router.push(`/contacts/edit/${this.contactId}`);
        }
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>
    
    <style scoped>
</style>
    