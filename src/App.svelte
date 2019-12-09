<svelte:head>
  <style src="theme.scss"></style>
</svelte:head>

<script>
    import Binput from './bulte/Binput.svelte';
    let form = {
        name: null
    };
</script>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>

<main>
    <h1>Bulte</h1>
    <p>A component exercise!</p>
    <Binput name="name" label="Name" placeholder="type your name here..." bind:value={form.name} isRounded/>
</main>
