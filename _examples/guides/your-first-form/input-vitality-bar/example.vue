<template>
<FormKit type="form" #default="{ value }" :actions="false">
  <!-- %partial%::html:: -->
  <FormKit
    type="range"
    name="strength"
    id="strength"
    label="Strength"
    value="5"
    min="1"
    max="10"
    step="1"
    help="How many strength points should this character have?"
  />

  <!-- %partial%::html:: -->
  <p><em><small>Remember: You have a budget of 20 points to build your character.</small></em></p>
  <pre wrap>{{ value.strength }}</pre>
</FormKit>
</template>

