<script>
	import Avatar from '$lib/Avatar.svelte';
    import Navbar from '$lib/Navbar.svelte';
</script>

<nav class="bg-white shadow dark:bg-gray-800">
    <div class="flex items-center justify-between lg:ml-10 md:ml-20 ml-5">
        <div class="flex items-center">
            <Avatar />
        </div>
        <div>
            <Navbar />
        </div>
    </div>
</nav>