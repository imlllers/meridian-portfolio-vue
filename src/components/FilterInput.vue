<template>
  <label class="root">
    <span class="label">{{ label }}</span>
    <input
      class="field"
      type="search"
      :value="modelValue"
      :placeholder="placeholder"
      @input="onInput"
    />
  </label>
</template>

<script>
export default {
  name: 'FilterInput',
  props: {
    modelValue: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      default: 'Поиск проектов',
    },
    placeholder: {
      type: String,
      default: 'Название или описание…',
    },
  },
  data() {
    return {};
  },
  methods: {
    onInput(event) {
      this.$emit('update:modelValue', event.target.value);
    },
  },
};
</script>

<style scoped>
.root {
  display: flex;
  flex-direction: column;
  gap: 8px;
  width: 100%;
}

.label {
  font-size: 12px;
  font-weight: 500;
  color: var(--color-dark);
}

.field {
  width: 100%;
  height: 48px;
  box-sizing: border-box;
  padding: 0 16px;
  border-radius: 12px;
  border: 1px solid var(--color-dark);
  background-color: transparent;
  color: var(--color-dark);
  font-family: inherit;
  font-size: 14px;
  outline: none;
  transition: border-color 0.15s ease;
}

.field::placeholder {
  color: var(--color-dark);
  opacity: 0.55;
}

.field:focus {
  border-color: var(--color-dark-blue);
}
</style>
