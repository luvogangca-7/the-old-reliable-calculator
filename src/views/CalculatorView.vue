<template>
    <div class="main-page">

        <div class="brand">
            <div class="logo">GANGCA</div>
            <div class="model"><em>00001</em></div>
        </div>

        <div class="screen">
            <div class="input">
                <p>{{ input }}</p>
            </div>
        </div>

        <div class="buttons">
            <button>9</button>
            <button>8</button>
            <button>7</button>
            <button class="ops">+</button>
            <button>6</button>
            <button>5</button>
            <button>4</button>
            <button class="ops">-</button>
            <button>3</button>
            <button>2</button>
            <button>1</button>
            <button class="ops">*</button>
            <button>0</button>
            <button><=</button>
            <button class="equal">=</button>
            <button class="ops">/</button>
        </div>
        
    </div>
</template>
<script>
export default {
    
}
</script>
<style>
    .main-page {
        height: 100%;
        width: 35vw;
        border-radius: 30px;
        background-color: rgb(111, 111, 111);
        justify-self: center;
        align-self: center;
        padding: 30px 20px;
    }
    .brand {
        display: flex;
        justify-content: space-between;
        color: white;
    }

    .brand .logo {

        font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
        font-weight: 900;
        letter-spacing: 2px;
    }

    .brand .model {
        font-family:'Times New Roman', Times, serif ;
    }

    .screen {
        margin-block: 10px;
        height: 200px;
        background-color: rgb(22, 22, 22);
        color: white;
        align-content: flex-end;
        padding: 10px;
    }

    .screen .input{
        text-align: end;
        font-size: 2.2rem;
    }

    .buttons {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        gap: 10px;
        padding-block: 20px;

    }

    .buttons button {
        height: 50px;
        border-radius: 8px;
        border: none;
        box-shadow: 0 4px 0 rgba(53, 53, 53, 0.8);
        font-size: 1.2rem;
        transition: transform 10ms ease-out;
    }

    .buttons button:active, .equal:active, .ops:active {
        transform: translateY(3px);
        box-shadow: none !important;
    }

    .equal {
        background-color: rgb(241, 106, 2);
        color:white;
        box-shadow: 0 4px 0 rgba(149, 65, 0, 0.8) !important;
    }

    .ops {
        background-color: rgb(15, 142, 167);
        color:white;
        box-shadow: 0 4px 0 rgba(1, 78, 93, 0.8) !important;
    }
</style>