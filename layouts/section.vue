<template>
  <div
    class="slidev-layout section flex flex-col items-center justify-center h-full"
  >
    <div class="my-auto text-center">
      <slot />
    </div>
  </div>
</template>

<style>
.section {
  background-color: var(--slidev-theme-primary);
  color: white;
}

.section h1,
.section h2 {
  color: white;
  font-size: 2.5em;
  font-weight: 600;
  margin-bottom: 0.5em;
}
</style>
