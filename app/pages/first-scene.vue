<script setup lang="ts"></script>

<template>
  <TresCanvas clear-color="#111" window-size preset="realistic">
    <Suspense>
      <LazyFirstScene />
    </Suspense>
  </TresCanvas>
</template>
