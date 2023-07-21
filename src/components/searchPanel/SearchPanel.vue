<template>
  <div>
    <input
      type="text"
      class="input"
      placeholder="kinolarni qidirish"
      :value="term"
      @input="changeTerm"
    />
  </div>
</template>
<script>
export default {
  props: {
    updateTerm: {
      type: Function,
      required: true,
    },
  },
  data() {
    return {
      term: "",
    };
  },
  methods: {
    changeTerm(e) {
      this.term = e.target.value;
      this.updateTerm(this.term)
    },
  },
};
</script>
<style>
.input {
  width: 100%;
  padding-top: 20px;
  padding-bottom: 20px;
  border-radius: 20px;
  border: 2px solid #013510;
  box-shadow: 10px 5px 5px rgb(1, 53, 16);
  font-size: 22px;
}
</style>