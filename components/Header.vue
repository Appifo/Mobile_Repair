<script setup lang="ts">
const links = [
  {
    label: 'Features',
    to: '#features',
    icon: 'i-heroicons-cube-transparent',
    exactHash: true
  },
  {
    label: 'Pricing',
    to: '#pricing',
    icon: 'i-heroicons-credit-card',
    exactHash: true
  },
  {
    label: 'Testimonials',
    to: '#testimonials',
    icon: 'i-heroicons-academic-cap',
    exactHash: true
  }
]
</script>

<template>
  <UHeader :links="links">
    <template #top>
      <AppBar />
    </template>

    <template #logo>
      <UIcon name="" class="ml-1 w-4 h-4 pointer-events-none" />
      <span>IRepair</span>
    </template>

    <template #right>
      <UButton label="Log in" color="white" variant="ghost" trailing-icon="i-heroicons-arrow-right-20-solid"
        class="hidden lg:flex" />
    </template>

    <template #panel>
      <UAsideLinks :links="links" />

      <UDivider class="my-6" />

      <UButton label="Sign in" color="white" block class="mb-3" />
      <UButton label="Get started" block />
    </template>
  </UHeader>
</template>
