
<template>


  <section>
    <div class="roles">
      <CardPerson
          :description="'User'"
          :avatar="'/images/user.png'"
          :button_caption="'CREATE'"
          :on-click-button-show="() => showFormRole('Team Member')"
          :on-click-button-hide="() => removeFormUser()"

      />

      <CardPerson
          :description="'Admin'"
          :avatar="'/images/admin.png'"
          :button_caption="'CREATE'"
          :on-click-button-show="() => showFormRole('Administrator')"
          :on-click-button-hide="() => removeFormUser()"
      />
    </div>

    <div class="form">
      <form-user v-if="showFormUser" :role="selectedRole"/>
    </div>




  </section>

</template>

<script setup>
  import { ref } from "vue"
  import CardPerson from "@/components/tools/CardPerson.vue";
  import formUser from "@/components/tools/formUser.vue";
  import CardProject from "@/components/tools/CardProject.vue";
  const showFormUser = ref(false);
  const selectedRole = ref(false);

  const showFormRole = (role) => {
    if (!showFormUser.value) {
      showFormUser.value = true;
    }
    selectedRole.value = role;
  }

  const removeFormUser = () => {
    if (showFormUser.value === true){
      showFormUser.value = !showFormUser.value;
    }
  }
</script>

<style scoped>

.roles{
  display: flex;
  flex-direction: row;
  justify-content: center;

}

.form{
  display: flex;
  justify-content: center;
}
.projects{
  margin-top: 5%;
  display: flex;
  justify-content: center;
}
</style>

