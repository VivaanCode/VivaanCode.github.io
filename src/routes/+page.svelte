<script lang="ts">
    import { onMount } from 'svelte';
    import { browser } from '$app/environment';
    
    let content = false;
    let header1 = !browser;
    let header2 = !browser;

    let subcard1: boolean = !browser;
    let subcard2: boolean = !browser;
    let subcard3: boolean = !browser;

    function extend() {
        const card = document.querySelector('.card') as HTMLElement;
        if (card) {
            card.classList.add('animate-extend');
        }
    }

    const delay = (ms: number) => new Promise(res => setTimeout(res, ms));

    onMount(async () => {
        await delay(75);   // Initial wait
        await delay(750);  // Logic wait
        content = true;
        
        await delay(200);
        header1 = true;
        
        await delay(200);
        header2 = true;
        
        await delay(450);
        extend();

        await delay(100);
        subcard1 = true;
        await delay(100);
        subcard2 = true;
        await delay(100);
        subcard3 = true;
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
        height: 120px;
        overflow: hidden;
        transition: height 0.45s ease;
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
    <h1 class="text-xl font-bold animate-fadeIn">vivaan</h1>
    </div>
{/if}

{#if content}
    <div class="main animate-fadeIn">
        <div class="card p-3 rounded-lg">

            <h1
                class="text-2xl font-bold opacity-0"
                class:animate-fadeIn={header1 ? 1 : 0}
            >Hey, I'm Vivaan</h1>

            <p 
                class:animate-fadeIn={header2 ? 1 : 0}
                style="opacity:0;"
                >An aspiring student and backend/fullstack developer.</p>

            <div class="subcardContainer flex m-0">
                <div class="subcard card p-3 rounded-lg w-30 m-4 ml-2 mr-2 opacity-0 cursor-pointer" class:animate-fadeIn={subcard1 ? 1 : 0}>
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                </div>

                <div class="subcard card p-3 rounded-lg w-30 m-4 ml-2 mr-2 opacity-0 cursor-pointer" class:animate-fadeIn={subcard2 ? 1 : 0}>
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                </div>

                <div class="subcard card p-3 rounded-lg w-30 m-4 ml-2 mr-2 opacity-0 cursor-pointer" class:animate-fadeIn={subcard3 ? 1 : 0}>
                    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.</p>
                </div>
            </div>
        </div>
    </div>
{/if}