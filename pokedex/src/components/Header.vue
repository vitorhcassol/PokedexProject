<template>
    <div id="header">
        <div class="wrapper">
            <img src="../img/Pokéball.png" alt="">
            <span>Pokédex</span>
            <img src="../img/Icon.png" alt="">
        </div>
    </div> 
</template>

<script>

</script>

<style scoped>
    #header {
        height: 7.2rem;
        
        background-color: var(--primary-color);
        
        color: var(--white);
        font-size: 2.4rem;
        font-family: 'Cantora One', sans-serif;
    }
    
    .wrapper {
        display: flex;
        justify-content: space-between;
        align-items: center;

        padding: 1.5rem 2.4rem;

        max-width: 76.8rem;

        margin: auto;
    }
</style>