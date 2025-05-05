<template>
  <div
    class="slidev-layout end flex flex-col items-center justify-center h-full"
  >
    <div class="my-auto text-center">
      <slot />
    </div>
  </div>
</template>

<style>
.end {
  background-color: var(--slidev-theme-primary);
  color: white;
  background-image: linear-gradient(
    to bottom right,
    var(--slidev-theme-primary),
    var(--slidev-theme-secondary, #2a679c)
  );
}

.end h1 {
  color: white;
  font-size: 4em;
  font-weight: 700;
  margin-bottom: 0.2em;
}
</style>
