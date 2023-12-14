<template>
    <div class="text-gray-500 dark:text-gray-400">
        <div class="h-[69px] flex justify-center items-center shadow-md bg-white dark:bg-gray-800">
            <NuxtLink class="ml-6 text-lg font-bold text-gray-800 dark:text-gray-200" to="/">
                <img 
                    src="/assets/img/logo.jpeg"
                    alt="Logo"
                    class="w-1/2"
                    loading="lazy" />

            </NuxtLink>
        </div>
        <ul class="mt-6">
            <sidebar-dashboard-menu />
            <sidebar-pages-menu />
        </ul>
        <!-- <sidebar-create-account /> -->
    </div>
</template>