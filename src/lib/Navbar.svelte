<script>
    import { page } from "$app/stores";
    import { browser } from "$app/environment";

    let menuAberto = false;

    const itemsMenu = [
        { href: "/", label: "Início" },
        { href: "/perfil", label: "Perfil" },
        { href: "/resumo", label: "Resumo" },
        { href: "/contatos", label: "Contatos" },
    ];
</script>

<nav class="flex flex-col sm:flex-row items-center gap-x-2 sm:gap-x-4 p-4">
    <div class="container px-6 py-4 mx-auto md:flex md:justify-between md:items-center">
        <div class="flex items-center justify-between w-full">
            <div class="flex justify-end lg:hidden w-full">
                <button type="button" on:click={() => menuAberto = !menuAberto} class="text-gray-500 dark:text-gray-200 hover:text-gray-600 dark:hover:text-gray-400 focus:outline-none focus:text-gray-600 dark:focus:text-gray-400" aria-label="toggle menu">
                    {#if menuAberto}
                        <!-- Ícone de fechar -->
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
                        </svg>
                    {:else}
                        <!-- Ícone de menu -->
                        <svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M4 8h16M4 16h16" />
                        </svg>
                    {/if}
                </button>
            </div>
        </div>

        <div class="{menuAberto ? 'flex' : 'hidden'} absolute inset-x-0 z-20 w-full px-6 py-4 transition-all duration-300 ease-in-out bg-white dark:bg-gray-800 md:mt-0 md:p-0 md:top-0 md:relative md:bg-transparent md:w-auto md:opacity-100 md:translate-x-0 md:flex md:items-center md:justify-between">
            <div class="flex flex-col md:flex-row md:mx-6">
                {#each itemsMenu as {href, label}}
                    <a href="{href}" on:click={() => { if (browser) { menuAberto = false; } }} class="mx-1.5 sm:mx-6 transition-colors duration-300 transform dark:text-gray-200 hover:text-gray-800 dark:hover:text-gray-200 hover:border-blue-500 {href === $page.url.pathname ? 'border-b-2 border-blue-500 text-gray-800' : 'border-b-2 border-transparent'}">{label}</a>
                {/each}
            </div>
        </div>
    </div>
</nav>

<!-- <script lang="ts">
	import { page } from "$app/stores";

    const itemsMenu = [
        { href: "/", label: "Início" },
        { href: "/perfil", label: "Perfil" },
        { href: "/resumo", label: "Resumo" },
        { href: "/contatos", label: "Contatos" },
    ];
</script>

{#each itemsMenu as {href, label}}
    {#if $page.url.pathname === href}
        <a {href} class="text-gray-800 transition-colors duration-300 transform dark:text-gray-200 border-b-2 border-blue-500 mx-1.5 sm:mx-6">{label}</a>
    {:else}
        <a {href} class="border-b-2 border-transparent hover:text-gray-800 transition-colors duration-300 transform dark:hover:text-gray-200 hover:border-blue-500 mx-1.5 sm:mx-6">{label}</a>
    {/if}
{/each}

<a href="/" class="border-b-2 border-transparent hover:text-gray-800 transition-colors duration-300 transform dark:hover:text-gray-200 hover:border-blue-500 mx-1.5 sm:mx-6">
    <svg class="w-4 h-4 fill-current" viewBox="0 0 640 512" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path 
            d="M392.8 1.2c-17-4.9-34.7 5-39.6 22l-128 448c-4.9 17 5 34.7 22 39.6s34.7-5 39.6-22l128-448c4.9-17-5-34.7-22-39.6zm80.6 120.1c-12.5 12.5-12.5 32.8 0 45.3L562.7 256l-89.4 89.4c-12.5 12.5-12.5 32.8 0 45.3s32.8 12.5 45.3 0l112-112c12.5-12.5 12.5-32.8 0-45.3l-112-112c-12.5-12.5-32.8-12.5-45.3 0zm-306.7 0c-12.5-12.5-32.8-12.5-45.3 0l-112 112c-12.5 12.5-12.5 32.8 0 45.3l112 112c12.5 12.5 32.8 12.5 45.3 0s12.5-32.8 0-45.3L77.3 256l89.4-89.4c12.5-12.5 12.5-32.8 0-45.3z">
        </path>
    </svg>
</a>

<a href="/" class="border-b-2 border-transparent hover:text-gray-800 transition-colors duration-300 transform dark:hover:text-gray-200 hover:border-blue-500 mx-1.5 sm:mx-6">
    <svg class="w-5 h-5 fill-current" viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg">
        <path 
            d="M404.2 309.5L383.1 344h42.3l-21.1-34.5zM371.4 256l-54-88H194.6l-54 88 54 88H317.4l54-88zm65.7 0l53.4 87c3.6 5.9 5.5 12.7 5.5 19.6c0 20.7-16.8 37.4-37.4 37.4H348.7l-56.2 91.5C284.8 504.3 270.9 512 256 512s-28.8-7.7-36.6-20.5L163.3 400H53.4C32.8 400 16 383.2 16 362.6c0-6.9 1.9-13.7 5.5-19.6l53.4-87L21.5 169c-3.6-5.9-5.5-12.7-5.5-19.6C16 128.8 32.8 112 53.4 112H163.3l56.2-91.5C227.2 7.7 241.1 0 256 0s28.8 7.7 36.6 20.5L348.7 112H458.6c20.7 0 37.4 16.8 37.4 37.4c0 6.9-1.9 13.7-5.5 19.6l-53.4 87zm-54-88l21.1 34.5L425.4 168H383.1zM283 112L256 68l-27 44h54zM128.9 168H86.6l21.1 34.5L128.9 168zM107.8 309.5L86.6 344h42.3l-21.1-34.5zM229 400l27 44 27-44H229z">
        </path>
    </svg>
</a> -->