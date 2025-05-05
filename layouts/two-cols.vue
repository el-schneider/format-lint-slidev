<template>
  <div class="slidev-layout two-cols w-full h-full">
    <div class="grid grid-cols-2 gap-4 w-full h-full">
      <div class="col-left">
        <slot />
      </div>
      <div class="col-right">
        <slot name="right" />
      </div>
    </div>
  </div>
</template>

<style>
.two-cols .col-left,
.two-cols .col-right {
  padding: 1rem;
}
</style>
