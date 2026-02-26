<script>
    import { onMount } from 'svelte';
    import { browser } from '$app/environment';
    
    let fade = !browser;
    let content = !browser;
    
    onMount(() => {
        setTimeout(() => {
            fade = true;
            setTimeout(() => {
                content = true;
            }, 750);
        }, 75);
    });
</script>

<style>
    /* @import url('https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&family=Roboto:ital,wght@0,1...'); */
    @reference "tailwindcss";

    :global(html, body) {
        background: #000;
        color: #fff;
        margin: 0;
        height: 100%;
    }

    .loader {
        position: absolute;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100vh;
        width: 100vw;
        top: 0;
        left: 0;
    }

    .main {
        min-height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .card {
        border: 1px solid rgba(255, 255, 255, 0.12);
        box-shadow: 0 8px 30px rgba(0, 0, 0, 0.45), 0 0 0 1px rgba(255, 255, 255, 0.04) inset;
        background: rgba(255, 255, 255, 0.03);
        backdrop-filter: blur(6px);
        padding: 24px 28px;
        border-radius: 14px;
        line-height: 1.5;
    }

    h1 {
        font-family: "Inter", sans-serif;
        margin: 0;
    }

    .card p {
        opacity: 0.75;
    }

</style>

{#if !content}
    <div class="loader absolute h-screen w-screen">
    </div>
{/if}

{#if content}
    <div class="main animate-fadeIn">
        <div class="card p-3 rounded-lg">
            <h1 class="text-xl font-bold">Hey, I'm Vivaan</h1>
            <p>idk what to put here</p>
        </div>
    </div>
{/if}