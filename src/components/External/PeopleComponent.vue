<template>
  <div>
    <h1>Descrição da pessoa : {{ people.name }}, ele tem {{ people.age }}</h1>
    <p>Utiliza as seguintes skills:</p>
    <ul>
      <li v-for="skill in people.skills" :key="skill.id">{{ skill.name }}</li>
    </ul>
    <form :ref="formSkill.ref" @submit.prevent="addSkill($event)">
      <InputComponent
        label="Teste"
        :placeholder="formSkill.inputPlaceholder"
        v-model="formSkill.inputValue"
      />
    </form>
  </div>
</template>

<script>
import InputComponent from "@/components/Form/Input/InputComponent.vue";

export default {
  components: {
    InputComponent,
  },
  name: "PeopleComponent",
  data() {
    return {
      formSkill: {
        ref: "formSkill",
        inputName: "skill_name",
        inputPlaceholder: "Nome da Skill",
        inputValue: null,
      },
      people: {
        name: "Alexandre Ferreira",
        age: 40,
        skills: [
          { id: 1, name: "PHP" },
          { id: 2, name: "Javascript" },
          { id: 3, name: "Vue" },
          { id: 4, name: "Python" },
          { id: 5, name: "Laravel" },
        ],
      },
    };
  },
  methods: {
    addSkill(e) {
      let lastSkill = this.people.skills.at(-1);
      this.people.skills.push({
        id: lastSkill.id + 1,
        name: this.formSkill.inputValue,
      });
      console.log(e);
    },
  },
};
</script>
