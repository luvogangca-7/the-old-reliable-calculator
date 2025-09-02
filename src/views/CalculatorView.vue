<template>
    <div class="main-page">

        <div class="brand">
            <div class="logo">GANGCA</div>
            <div class="model"><em>00001</em></div>
        </div>

        <div class="screen">
            <div class="input">
                <input type="text" v-if="typing" v-model="input">
                <p class="answer" v-else>{{ answer }}</p>

            </div>
        </div>

        <div class="buttons">
            <button :value="inputs.ops[4]" @click="typeValue(inputs.ops[4])">{{ inputs.ops[4] }}</button>
            <button :value="inputs.ops[5]" @click="typeValue(inputs.ops[5])">{{ inputs.ops[5] }}</button>
            <button :value="inputs.back" @click="backspace()">{{ inputs.back }}</button>
            <button class="clear" @click="clear()">C</button>
            <button :value="inputs.nums[9]" @click="typeValue(inputs.nums[9])">{{ inputs.nums[9] }}</button>
            <button :value="inputs.nums[8]" @click="typeValue(inputs.nums[8])">{{ inputs.nums[8] }}</button>
            <button :value="inputs.nums[7]" @click="typeValue(inputs.nums[7])">{{ inputs.nums[7] }}</button>
            <button class="ops" :value="inputs.ops[0]" @click="typeValue(inputs.ops[0])">{{ inputs.ops[0] }}</button>
            <button :value="inputs.nums[6]" @click="typeValue(inputs.nums[6])">{{ inputs.nums[6] }}</button>
            <button :value="inputs.nums[5]" @click="typeValue(inputs.nums[5])">{{ inputs.nums[5] }}</button>
            <button :value="inputs.nums[4]" @click="typeValue(inputs.nums[4])">{{ inputs.nums[4] }}</button>
            <button class="ops" :value="inputs.ops[1]" @click="typeValue(inputs.ops[1])">{{ inputs.ops[1] }}</button>
            <button :value="inputs.nums[3]" @click="typeValue(inputs.nums[3])">{{ inputs.nums[3] }}</button>
            <button :value="inputs.nums[2]" @click="typeValue(inputs.nums[2])">{{ inputs.nums[2] }}</button>
            <button :value="inputs.nums[1]" @click="typeValue(inputs.nums[1])">{{ inputs.nums[1] }}</button>
            <button class="ops" :value="inputs.ops[2]" @click="typeValue(inputs.ops[2])">{{ inputs.ops[2] }}</button>
            <button :value="inputs.nums[0]" @click="typeValue(inputs.nums[0])">{{ inputs.nums[0] }}</button>
            <button :value="inputs.ops[6]" @click="typeValue(inputs.ops[6])">{{ inputs.ops[6] }}</button>
            <button class="equal" @click="evaluate(input)">{{ inputs.ans }}</button>
            <button class="ops" :value="inputs.ops[3]" @click="typeValue(inputs.ops[3])">{{ inputs.ops[3] }}</button>
        </div>
        
    </div>
</template>
<script>

export default {
    data(){
        return {
            inputs:{
                nums:[0,1,2,3,4,5,6,7,8,9],
                ops:['+','-','*','/','(',')','.'],
                ans:'=',
                back:'<='
            },
            input:'',
            answer:'',
            typing:true
        }  
    },
    methods:{
        typeValue(value){
            if(!this.typing){
                this.input = ''
                this.typing = true
            }
            
            this.input += value        
        },
        evaluate(expr){

            try {
                
                expr = expr.replace(/(\d)(\()/g, '$1*$2');
                expr = expr.replace(/(\))(\d)/g, '$1*$2');
                expr = expr.replace(/(\))(\()/g, '$1*$2');

                this.answer = String(eval(expr))
          
            } catch (error) {
                this.answer = 'ERROR' 
            }
            this.typing = false

        return this.answer
    },
    backspace(){
        this.input = this.input.slice(0, -1)
    },
    clear(){
        this.input = ''
        this.answer = ''
        this.typing = true
    }
    }
    
}
</script>
<style>
    .main-page {
        height: 100%;
        min-width: 280px;
        width: 35vw;
        border-radius: 30px;
        background-color: rgb(111, 111, 111);
        justify-self: center;
        align-self: center;
        padding: 30px 20px;
        box-shadow: 0 20px 0 rgba(21, 21, 21, 0.4);
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

    .screen input, .screen p{
        background: transparent;
        border: none;
        color: white;
        text-align: end;
        font-size: 2.2rem;
    }

    .screen input {
        width: 100%;
    }
    
    .screen input:focus {
        outline:none;
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
        font-size: 1.7rem;
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

    .clear {
        background-color: #171717;
        color:white;
        box-shadow: 0 4px 0 rgba(14, 14, 14, 0.8) !important;
    }

   /* @media (max-width: 600px) {
        .main-page{
            width: 80vw; 
        }

    } */
</style>