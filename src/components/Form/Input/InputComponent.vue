<template>
  <div>
    <label :for="id">{{ label }}</label>
    <input
      :id="id"
      :type="type"
      :value="value"
      @input="updateValue($event.target.value)"
    />
  </div>
</template>

<script>
export default {
  name: "InputComponent",
  props: {
    label: {
      type: String,
      required: true,
    },
    type: {
      type: String,
      default: "text",
    },
    value: {
      type: String,
      default: "",
    },
    placeholder: {
      type: String,
      default: "",
    },
  },
  data() {
    return {
      id: "input-" + Math.random().toString(36).substr(2, 10),
    };
  },
  methods: {
    updateValue(newValue) {
      this.$emit("input", newValue);
    },
  },
};
</script>

<style scoped src="./style.css" lang="css"></style>