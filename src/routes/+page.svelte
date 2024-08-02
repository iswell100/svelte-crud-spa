<script>
    import { onMount } from 'svelte';

    let post = null;
    let error = null;

    onMount(async () => {
        try {
            const res = await fetch('http://fakestoreapi.com/products'); // Ganti dengan URL API Anda
            if (!res.ok) {
                throw new Error('Network response was not ok');
            }
            post = await res.json();
        } catch (e) {
            error = e.message;
        }
    });
</script>

{#if error}
    <p>Error: {error}</p>
{:else if post}
    <ul>
        {#each post as item}
            <li>{item.title}</li> <!-- Ganti dengan data yang sesuai dari API -->
        {/each}
    </ul>
{:else}
    <p>Loading...</p>
{/if}


<div class="p-5 mb-4 bg-light rounded-3 shadow-sm border-0">
    <div class="container-fluid py-5">
        <h2 class="display-6 fw-bold">LARAVEL + SVELTE KIT </h2>
        <p class="col-md-8 fs-4">Belajar Laravel dengan Svelte KIT di SantriKoding.com</p>
        <a href="https://santrikoding.com/kategori/svelte" target="_blank" class="btn btn-primary btn-lg" type="button">Selengkapnya</a>
    </div>
</div>