<template>

  <div class="select-group">
      <select v-model="modelValue" @change="changeOptions">
          <option value="" disabled>Select a value:</option>
          <option 
                v-for="option in options" 
                :key="option.value" 
                value="option.value"
            >
            {{ option.name }}   
            </option>
      </select>
      <div class="select-icon">
        <svg focusable="false" viewBox="0 0 104 128" width="25" height="35" class="icon">
            <path d="m2e1 95a9 9 0 0 1 -9 9 9 9 0 0 1 -9 -9 9 9 0 0 1 9 -9 9 9 0 0 1 9 9zm0-3e1a9 9 0 0 1 -9 9 9 9 0 0 1 -9 -9 9 9 0 0 1 9 -9 9 9 0 0 1 9 9zm0-3e1a9 9 0 0 1 -9 9 9 9 0 0 1 -9 -9 9 9 0 0 1 9 -9 9 9 0 0 1 9 9zm14 55h68v1e1h-68zm0-3e1h68v1e1h-68zm0-3e1h68v1e1h-68z"></path>
        </svg>
        </div>
  </div>
</template>

<script>
export default {
    name: 'my-select',
    props: {
        modelValue: {
            type: String
        },
        options: {
            type: Array,
            default: () => []
        } 
    },
    methods: {
        changeOptions(event) {
            this.$emit('update:modelValue', event.target.value)
        }
    }
}
</script>

<style>

.select-group {
    position: relative;
}

select {
  min-width: 350px;
  width: 100%;
  height: 50px;
  font-size: 100%;
  font-weight: bold;
  cursor: pointer;
  border-radius: 0;
  background-color: #c0392b;
  border: none;
  border-bottom: 2px solid #962d22;
  color: white;
  padding: 10px;
  appearance: none;
  -webkit-appearance: none;
  -moz-appearance: none;
  padding: 10px;
}
/* For IE <= 11 */
select::-ms-expand {
  display: none; 
}

select:hover,
select:focus {
  color: #000000;
  background-color: white;
  border-bottom-color: #DCDCDC;
}

.select-icon {
  position: absolute;
  top: 4px;
  right: 4px;
  width: 40px;
  height: 36px;
  pointer-events: none;
  border: 2px solid #962d22;
  padding-left: 5px;
  transition: background-color 0.3s ease, border-color 0.3s ease;
}
.select-icon svg.icon {
  transition: fill 0.3s ease;
  fill: white;
}

select:hover ~ .select-icon,
select:focus ~ .select-icon {
  background-color: white;
  border-color: #DCDCDC;
}
select:hover ~ .select-icon svg.icon,
select:focus ~ .select-icon svg.icon {
  fill: #c0392b;
}

</style>