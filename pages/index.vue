<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">Nuxt Mission</h1>

      <!-- <pre>{{ $data }}</pre>
      <button class="button--green" @click="showPlanets">Show Planets</button> -->
      <!--auto component-->
      <PlanetsList />

      <!--lazy loading -->
      <!--<div v-if="show">
        <LazyPlanetsList />
      </div>-->
    </div>
  </div>
</template>
