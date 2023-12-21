<script setup lang="ts">
const links = [
  {
    label: 'Contacts',
    children: [
      {
        label: 'Email: support@irepair.com'
      },
      {
        label: 'Phone: (999) 444 9999'
      }
    ]
  },
  // {
  //   label: 'Features',
  //   children: [
  //     {
  //       label: 'Broken Display Repair'
  //     }, {
  //       label: 'Battery Replacement'
  //     }
  //   ]
  // }
]

const toast = useToast()

const email = ref('')
const loading = ref(false)

function onSubmit() {
  loading.value = true

  setTimeout(() => {
    toast.add({
      title: 'Subscribed!',
      description: 'You\'ve been subscribed to our newsletter.'
    })

    loading.value = false
  }, 1000)
}
</script>

<template>
  <UFooter>
    <template #top>
      <UFooterColumns :links="links">
        <template #right>
          <form @submit.prevent="onSubmit">
            <UFormGroup label="Subscribe to our newsletter" :ui="{ container: 'mt-3' }">
              <UInput v-model="email" type="email" placeholder="Enter your email"
                :ui="{ icon: { trailing: { pointer: '' } } }" required size="xl" autocomplete="off" class="max-w-sm">
                <template #trailing>
                  <UButton type="submit" size="xs" :label="loading ? 'Subscribing' : 'Subscribe'" :loading="loading" />
                </template>
              </UInput>
            </UFormGroup>
          </form>
        </template>
      </UFooterColumns>
    </template>

    <template #left>
      <p class="text-gray-500 dark:text-gray-400 text-sm">
        Copyright © {{ new Date().getFullYear() }}. All rights reserved.
      </p>
    </template>

    <template #right>
      <UColorModeButton size="sm" />

      <UButton to="https://www.facebook.com/" target="_blank" icon="i-simple-icons-facebook"
        aria-label="Facebook" color="gray" variant="ghost" />
    </template>
  </UFooter>
</template>
