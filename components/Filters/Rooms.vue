<template>
  <FiltersPopover v-model="isOpen">
    <Button @click="isOpen = !isOpen">
      <span>Liczba pokoi</span>
      <span v-if="from">od {{ from }}</span>
      <span v-if="to">do {{ to }}</span>
      <Icon name="radix-icons:triangle-down" />
    </Button>
    <template #panel>
      <div class="rooms">
        <Input v-model="from" type="number" />
        <div>do</div>
        <Input v-model="to" type="number" />
      </div>
    </template>
  </FiltersPopover>
</template>

<script lang="ts" setup>
const isOpen = ref(false);

const from = defineModel<number | undefined>('from');
const to = defineModel<number | undefined>('to');
</script>

<style lang="scss" scoped>
@use 'assets/scss/_variables';

.rooms {
  font-family: variables.$font;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;

  @media (max-width: variables.$break-point) {
    flex-wrap: wrap;
  }
}
</style>
