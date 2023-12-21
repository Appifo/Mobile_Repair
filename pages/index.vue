<script setup lang="ts">
const { data: page } = await useAsyncData('index', () => queryContent('/').findOne())

useSeoMeta({
  title: page.value.title,
  ogTitle: page.value.title,
  description: page.value.description,
  ogDescription: page.value.description
})

defineOgImage({
  component: 'Landing',
  title: page.value.title,
  description: page.value.description
})
</script>

<template>
  <div>
    <UContainer>
      <UPageHero :title="page.hero.title" :description="page.hero.description" align="left" :links="page.hero.links">
        <img src="/hero_img.jpg" class="w-full h-96 rounded-md shadow-xl ring-1 ring-gray-300 dark:ring-gray-700">
      </UPageHero>
    </UContainer>

    <ULandingSection id="features" :title="page.features.title" :description="page.features.description"
      :headline="page.features.headline">
      <UPageGrid>
        <ULandingCard v-for="(item, index) in page.features.items" :key="index" v-bind="item">
          <template #icon>
            <img :src="`/services/${item.img}`" class="w-12">
          </template>
        </ULandingCard>
      </UPageGrid>
    </ULandingSection>

    <ULandingSection id="pricing" :title="page.pricing.title" :description="page.pricing.description"
      :headline="page.pricing.headline">
      <UPricingGrid compact>
        <UPricingCard v-for="(plan, index) in page.pricing.plans" :key="index" v-bind="plan" />
      </UPricingGrid>
    </ULandingSection>

    <ULandingSection id="testimonials" :headline="page.testimonials.headline" :title="page.testimonials.title"
      :description="page.testimonials.description">
      <UPageColumns class="xl:columns-4">
        <div v-for="(testimonial, index) in page.testimonials.items" :key="index" class="break-inside-avoid">
          <ULandingTestimonial v-bind="testimonial" />
        </div>
      </UPageColumns>
    </ULandingSection>
  </div>
</template>
