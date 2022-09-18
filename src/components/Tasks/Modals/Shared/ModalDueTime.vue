<template>
  <div class="row q-mb-sm">
    <q-input
      class="col"
      outlined
      label="Due Time"
      :value="dueTime"
      v-model="dueTime"
    >
      <template v-slot:append>
        <q-icon
          v-if="dueTime"
          @input="$emit('update:dueTime', $event)"
          name="close"
          @click="$emit('update:dueTime', '')"
          class="cursor-pointer"
        />
        <q-icon name="access_time" class="cursor-pointer">
          <q-popup-proxy cover transition-show="scale" transition-hide="scale">
            <q-time :value="dueTime"
            @input="$emit('update:dueTime', $event)" />
          </q-popup-proxy>
        </q-icon>
      </template>
    </q-input>
  </div>
</template>

<script>
export default {
    props : ['dueTime'],
};
</script>

<style>
</style>