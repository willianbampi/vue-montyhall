<template>
    <div id="app">
        <h1>Problema de Monty Hall</h1>
        <div class="form">
            <div v-if="!started">
                <input type="text" id="portsAmount" 
                       v-model.number="portsAmount"
                       placeholder="Quantidade de portas">
            </div>
            <div v-if="!started">
                <input type="text" id="selectedPort" 
                       v-model.number="selectedPort" 
                       placeholder="Porta premiada">
            </div>
            <button v-if="!started" @click="started = true">Iniciar</button>
            <button v-if="started" @click="started = false">Reiniciar</button>
        </div>
        <div class="doors" v-if="started">
            <div v-for="port in portsAmount" :key="port">
                <Door :hasGift="port === selectedPort" :number="port"></Door>
            </div>
        </div>
    </div>
</template>

<script>

    import Door from './components/Door'

    export default {
        name: 'App',
        components: { Door },
        data: function() {
            return {
                started: false,
                portsAmount: null,
                selectedPort: null
            }
        }
    }

</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Montserrat', sans-serif;
    }

    body {
        color: #FFF;
        background: #19547b;
        background: -webkit-linear-gradient(to right, #19547b, #9b9181);
        background: linear-gradient(to right, #19547b, #9b9181);
    }

    #app {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    #app h1 {
        background-color: #0004;
        padding: 20px;
        margin-bottom: 60px;
    }

    .form {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin-bottom: 40px;
    }

    .form, 
    .form input, 
    .form button {
        margin-bottom: 10px;
        font-size: 1.2rem;
        border: none;
        outline: none;
        padding: 5px;
    }

    .form button {
        width: 150px;
        height: 50px;
    }

    .form label {
        margin-right: 10px;
    }

    .doors {
        align-self: stretch;
        display: flex;
        justify-content: space-around;
        flex-wrap: wrap;
    }
</style>
