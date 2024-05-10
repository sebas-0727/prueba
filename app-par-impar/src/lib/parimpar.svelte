<script>
    import App from "../App.svelte";

    export let numero ;
    let resultado;
    $: if (numero===0)
        resultado="neutro";
    else
        if (numero%2===0)
            resultado="par"
        else
            resultado="impar"
</script>

<p>El numero {numero} es {resultado} </p>

<style>
    p{
        color: white;
        font-family: 'segoe UI', Tahoma, geneva, verdana, sans-serif;
        font-size: 25px;
    }
</style>