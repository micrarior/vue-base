<template>
  <div
    class="form-group"
    :attribute="field.attribute"
    :class="[errorClasses, layoutClassResolved]">
    <label
      v-if="showLabel"
      :for="field.attribute">
      {{ fieldLabel || field.label }}
      <form-asterisk v-if="field.required"/>
    </label>
    <label
      v-else class="placeholder-label"
      :for="field.attribute">
      &nbsp;
    </label>
    <slot name="field"/>
    <slot name="errors">
      <div
        v-if="hasError"
        v-html="errorMessages"
        class="invalid-feedback d-block">
      </div>
    </slot>
    <small
      v-if="showHelpText && field.helpText"
      class="form-text text-muted">
      {{ field.helpText }}
    </small>
  </div>
</template>

<script>
  import FieldLayoutMixin from "../mixins/FieldLayoutMixin";

  export default {
    mixins: [FieldLayoutMixin]
  }
</script>

<style type="text/scss" scoped>
  .placeholder-label {
    display: none;
  }

  .col .placeholder-label {
    display: block;
  }

  [class*=" col-"] .placeholder-label {
    display: block;
  }
</style>
