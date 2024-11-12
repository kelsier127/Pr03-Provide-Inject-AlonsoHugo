<script setup>
    import { inject, watch } from 'vue'

    let arrayProductes=[
        { name: "Hamburger 🍔", price: 5 },
        { name: "Cheeseburger 🧀", price: 6 },
        { name: "Impossible Burger 🥕", price: 7 },
        { name: "Fries 🍟", price: 2 }
    ]
    let arrayFinal=[]

    let arrayCarrito = []

    let pepin = inject("monedaId")
    
    watch(pepin, onPepinChange)
    console.log("La variable de ListaProductos es: "+ pepin.value)

    function onPepinChange(){
        arrayFinal = []
        console.log(pepin.value)
        if(pepin.value=="€"){
            for(let i in arrayProductes){
                arrayProductes[i].price = (arrayProductes[i].price *= 0.92).toFixed(2);
                console.log(arrayProductes[i].price)
            }   
        }else if(pepin.value=="$"){
            for(let i in arrayProductes){
                arrayProductes[i].price = (arrayProductes[i].price /= 0.92).toFixed(2);
                console.log(arrayProductes[i].price)
            }   
        }
        
        console.log("Pepin ha cambiado")
    }

    function afegirCarret(nom, preu){
        let articulo=` ${nom} - ${preu}${pepin.value}`
        arrayCarrito.push(articulo)
        console.log(arrayCarrito)
    }

    function mostrarCarret(){
        window.alert(`Pepín, has comprado: ${arrayCarrito.toString()}`)
    }
</script>

<template>
        <section id="contenedorLista">
            <h3>Articles a la venda:</h3>
            <article v-for="item in arrayProductes" :key="item">
                <div id="divProducto">
                    <p> {{ item.name }} </p> 
                    <p>{{ item.price }}{{ pepin }}</p> 
                </div>
            
                <button @click="afegirCarret(item.name,item.price)">Afegir al carret</button>
            </article>
            <button @click="mostrarCarret">Qué he comprado?</button>

        </section>
</template>

<style scoped>
article{
    border-radius: 10px;
    margin: 5px;
    margin-bottom: 15px;
    padding:10px;
    background-color: aliceblue;
}

#divProducto{
    display: flex;
}

button{
    border-radius: 7px;
    border:0.3px solid white;
    background-color: rgb(111, 200, 248) ;
    transition: 0.4s;
}

button:hover{
    background-color: rgb(87, 170, 235) ;
}

button:active{
    background-color: rgb(0, 129, 228) ;
}

#contenedorLista{
    padding: 15px;
    background-color: rgb(165, 200, 230);
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    justify-items: center;
    justify-content: center;
}
</style>