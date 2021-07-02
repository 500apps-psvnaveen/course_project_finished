<template>
  <div>
    <button :type="type" :class="mode">
      <slot></slot>
    </button>
  </div>
</template>

<script>
export default {
  props: ['type', 'mode'],
};
</script>

<style scoped>
/* button {
  border: none;
  color: white;
  background-color: gray;
  font-size: 20px;
  padding: 10px;
  width: 100px;
  border-radius: 5px;
  outline: none;
}

button:hover {
  color: gray;
  background-color: white;
  text-shadow: 0px 0px 5px red;
  border: 1px solid grey;
} */

div {
  display: inline;
}

button {
  padding: 0.75rem 1.5rem;
  font-family: inherit;
  background-color: #3a0061;
  border: 1px solid #3a0061;
  color: white;
  cursor: pointer;
}

button:hover,
button:active {
  background-color: #270041;
  border-color: #270041;
}

.flat {
  background-color: transparent;
  color: #3a0061;
  border: none;
}

.flat:hover,
.flat:active {
  background-color: #edd2ff;
}
</style>