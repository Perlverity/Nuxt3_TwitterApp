<template>
  <div :class="{ 'dark': darkMode }">
    <div class="bg-white dark:bg-dim-900">
      <div class="min-h-full">
        <div class="grid grid-cols-12 mx-auto sm:px-6 lg:max-w-7xl lg:px-8 lg:gap-5">
            <!--   左サイドバー   -->
            <div class="md:block xs-col-span-1 xl:col-span-2">
              <div class="sticky top-8">
                <SidebarLeft />
              </div>
            </div>
            <!--   メインコンテンツ   -->
            <main class="col-span-12 md:col-span-8 xl:col-span-6">
              <router-view />
            </main>

            <!--   右サイドバー   -->
            <div class="hidden col-span-12 md:block xs-col-span-1 xl:col-span-4 md:col-span-3">
              <div class="sticky top-8">
                <SidebarRight />
              </div>
            </div>

        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const darkMode = ref(false)

</script>