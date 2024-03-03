<script lang="ts">
    export let data;
    let currentCategory = 'Todos';
    let resumoItems = data.items;

    function changeCategory(newCategory: string) {
        currentCategory = newCategory;
        filterResumo()
    }
    
    function filterResumo() {
        resumoItems = data.items.filter(item => {
            return item.category === currentCategory || currentCategory === 'Todos';
        })
    }
</script>

<section class="bg-white dark:bg-gray-900">
    <div class="container px-6 py-12 mx-auto">
         <div class="mt-8 xl:mt-16 lg:flex lg:-mx-12">
            <div class="lg:mx-12">
                <h1 class="text-xl font-semibold text-gray-800 dark:text-white">Resumo</h1>

                <div class="mt-4 space-y-4 lg:mt-8">
                    {#each data.categories as category}
                        {#if currentCategory === category}
                            <button class="block text-blue-500 dark:text-blue-400 hover:underline">{category}</button>
                        {:else}
                            <button on:click={() => {changeCategory(category)}} class="block text-gray-500 dark:text-gray-300 hover:underline">{category}</button>
                        {/if}
                    {/each}
                </div>    
            </div>

            <div class="flex-1 mt-8 lg:mx-12 lg:mt-0">
                <div class="grid grid-cols-1 gap-8 md:grid-cols-2 xl:grid-cols-3 ">
                    {#each resumoItems as {title, category, image}}
                        <div>
                            <img class="object-cover w-full rounded-lg h-96 "
                                src="{image}"
                                alt="">
                            <h2 class="mt-4 text-xl font-semibold text-gray-800 capitalize dark:text-white">{title}</h2>
                            <p class="mt-2 text-lg tracking-wider text-blue-500 uppercase dark:text-blue-400 ">{category}</p>
                        </div>
                    {/each}
                </div>
            </div>
        </div>
    </div>
</section>