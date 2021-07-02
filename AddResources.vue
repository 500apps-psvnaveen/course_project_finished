<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>
        Please check all inputs and make sure you enter at least a few
        characters into each input field.
      </p>
    </template>
    <template #actions>
      <base-button @click="confirmError">Okay</base-button>
    </template>
  </base-dialog>
  <base-card>
    <!-- <lable forid: <input type="text" ref="input0" /> <br /><br />
    name: <input type="text" ref="input1" /><br /><br />
    description: <input type="textarea" ref="value2" /><br /><br />
    link: <input type="url" ref="value3" /> -->
    <!-- <button @click="storeValueFunction">Add</button> -->
    <form @submit.prevent="storeValueFunction">
      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" ref="value0" />
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea
          id="description"
          name="description"
          rows="3"
          ref="textValue1"
        ></textarea>
        <!-- <input
          type="textarea"
          name="description"
          id="description"
          ref="textValue1"
        /> -->
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="url" ref="value2" />
      </div>
      <div>
        <base-button type="submit">Add Resource</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog },
  data() {
    return {
      inputIsInvalid: false,
      // value0: '',
      // value1: '',
      // value2: '',
      // value3: '',
    };
  },
  inject: ['addResource'],
  methods: {
    storeValueFunction() {
      const entTitle = this.$refs.value0.value;
      const entDes = this.$refs.textValue1.value;
      const entLin = this.$refs.value2.value;

      if (entTitle === '' || entDes === '' || entLin === '') {
        this.inputIsInvalid = true;
      } else {
        this.addResource(entTitle, entDes, entLin);
      }

      // this.value3 = this.$refs.value3.value;
      // this.$emit('inputs-values', entTitle, entDes, entLin);
    },
    confirmError() {
      this.inputIsInvalid = false;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>