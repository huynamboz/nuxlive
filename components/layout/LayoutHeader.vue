<script setup lang="ts">
const navbar = ref<HTMLElement | null>(null)
onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})
onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})

function handleScroll(): void {
  if (!navbar.value)
    return
  const navbarOffsetBottomWithPadding = navbar.value.offsetHeight + 20
  if (!navbar.value)
    return
  const scrollY = window.scrollY
  if (scrollY > navbarOffsetBottomWithPadding) {
    navbar.value.classList.add(
      'bg-white/70',
      'border-b-[1px]',
      'dark:bg-slate-900/80',
      'backdrop-blur',
    )
  }
  else {
    navbar.value.classList.remove(
      'bg-white/70',
      'border-b-[1px]',
      'dark:bg-slate-900/80',
      'backdrop-blur',
    )
  }
}
</script>

<template>
  <div
    ref="navbar"
    class="fixed top-0 flex left-0 w-full border-b border-shade-4 bg-shade-1 z-40 pl-[260px] h-[80px]"
  >
    <div class="flex-1 w-full h-full flex items-center justify-between px-5">
      <div>
        <Icon name="solar-square-alt-arrow-left-linear" class="text-2xl text-shade-6" />
      </div>
      <div class="flex items-center gap-5">
        <div class="p-[10px] flex justify-center items-center">
          <Icon name="solar-bell-linear" class="text-shade-9" size="20"/>
        </div>
        <BaseButton size="md" state="default" icon="no">
          Create
        </BaseButton>
        <BaseUserProfilePopup />
      </div>
    </div>
  </div>
</template>
