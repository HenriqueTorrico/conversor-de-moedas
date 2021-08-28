<template>
    <div class="conversor">
        <h2>{{ moedaA }} Para {{ moedaB}}</h2>
        <input type="number" v-model="moedaA_valor" v-bind:placeholder="moedaA">
        <input type="button" value="Converter" v-on:click="converter">
        <h2>{{ moedaB_valor }}</h2>
    </div>
</template>

<script>
export default {
    name: "Conversor",
    props: ["moedaA", "moedaB"],
    data() {
        return {
            moedaA_valor: "",
            moedaB_valor: 0       
        }
    },
    methods: {
        converter() {
            let de_para = this.moedaA + "_" + this.moedaB;
            let url = "https://free.currconv.com/api/v7/convert?q=" + de_para + "&compact=ultra&apiKey=adb0dd5f9bafa3c6d76b";

            fetch(url)
                .then(resposta => {
                    return resposta.json()
                })
                .then(json => {
                    let cotacao = json[de_para];
                    this.moedaB_valor = (cotacao * parseFloat(this.moedaA_valor)).toFixed(2);
                })
        }
    }
}
</script>

<style scoped>
    .conversor {
        padding: 30px 50px;
        max-width: 300px;
        box-shadow:  0 4px 8px 0 rgba(0, 0, 0, 0.2);
    }

    .conversor h2 {
        font-size: 24px;
    }

    .conversor input {
        outline: none;
        display: block;
        border: none;
        border-radius: 5px;
        font-size: 17px;
    }

    .conversor input[type=number] {
        padding: 13px ;
        background: rgb(250, 247, 247);      
        box-sizing: border-box;
        margin: 0 auto;
        text-align: center;
    }

    .conversor input[type=button] {
        border: 2px solid #2c3e50;
        background: #fff;
        margin: 23px auto;
        padding: 10px 50px;
        cursor: pointer;       
        text-align: center;
    }

    .conversor input[type=button]:hover {
        background: #2c3e50;
        color: #fff;
        transition: 0.6s;
    }

     @media(max-width: 320px){
        .conversor input[type=number] {
            margin-left: 0;
            padding: 13px 10px;
            max-width: 180px;
        }
     }
</style>