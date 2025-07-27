<script setup lang="ts">
import {
  OrbitControls,
  Plane,
  Sphere,
  Box,
  Environment,
} from "@tresjs/cientos";

const { scene } = useTresContext();

const { onLoop } = useRenderLoop();

onLoop(() => {
  scene.value.backgroundRotation.y += 0.01;
  scene.value.environmentRotation.y += 0.01;
});
</script>

<template>
  <Sphere :args="[0.5, 32, 16]" :position="[0, 3, 0]" cast-shadow>
    <TresMeshStandardMaterial color="lightblue" />
  </Sphere>

  <Box :args="[1, 1, 1]" :position="[0, 1.5, 0]" cast-shadow receive-shadow>
    <TresMeshStandardMaterial color="orange" />
  </Box>

  <Sphere :position="[2, 1, 0]" :args="[0.5, 32, 16]" cast-shadow>
    <TresMeshStandardMaterial color="orange" :roughness="0.1" />
  </Sphere>

  <Plane :position="[0, 0, 0]" :args="[10, 10, 10, 10]" receive-shadow>
    <TresMeshStandardMaterial color="teal" />
  </Plane>

  <Environment preset="city" sync-materials />
  <!-- <TresAmbientLight />
  <TresDirectionalLight :position="[2, 4, 2]" :intensity="10" cast-shadow /> -->

  <!-- <SoftShadows /> -->

  <TresGridHelper />
  <TresPerspectiveCamera :position="[2, 5, 7.5]" />
  <OrbitControls />
</template>
