<script lang="js">
    import Nested from "./Nested.svelte"
    let name = "Svelte"
</script>

<h1>Hello, {name.toUpperCase()}</h1>

<p>This a paragraph.</p>
<Nested />

<style>
    p {
        color: goldenrod;
        font-family: 'Comic Sans MS';
        font-size: 2em;
    }
</style>