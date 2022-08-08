<template>
<div class="coffees" @click.self="actualIndex = null">
    <fa class="coffees--left" icon="arrow-left"
    @click="prev"/>
    <fa class="coffees--right" icon="arrow-right"
    @click="next"/>

    <div class="coffees__slider" @click.self="actualIndex = null">
        
        <div v-for="(coffee, i) in showed" :key="i"
        class="coffees__card"
        ref="card"
        @click="handleToggle(i)"
        :class="actualIndex == i ? 'actual':''">

            <div class="coffees__img">
                <img :src="require(`../assets/${coffee.img}`)" alt="Coffee :)"
                :style="coffee.img == 'coffee2.png'? 'margin-bottom:-25px; transform:scale(0.85)':''"
                :class="coffee.img == 'coffee4.png'? 'bigger':''">
            </div>

            <h1>{{coffee.name}}</h1>

            <div v-if="actualIndex != i">
                <span v-for="details in coffee.calories" :key="details.fat">
                    <h4>{{details.fat}}</h4>
                    <p>{{details.satured}}</p>
                    <p>{{details.trans}}</p>
                </span>
            </div>

            <div v-show="actualIndex == i" class="coffees__selects">

                <div class="coffees__size">
                    <h2>Size</h2>
                    <select id="cars" name="cars">
                        <option value="demi">Demi</option>
                        <option value="short">Short</option>
                        <option value="Tall">Tall</option>
                        <option value="Grande">Grande</option>
                        <option value="Venti">Venti</option>
                    </select>
                </div>

                <div class="coffees__milk">
                    <h2>Milk</h2>
                    <select id="cars" name="cars">
                        <option value="cremoso">Cremoso</option>
                        <option value="aveia">Aveia</option>
                        <option value="vegetal">Vegetal</option>
                    </select>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
    data(){
        return{
            productList:[
                {name:'Frapuccino', calories:[
                    {fat: 'Total fat 13g'},
                    {satured: 'Satured fat 9g'},
                    {trans: 'Trans fat 0g'}
                ],img:'coffee1.png', show:true},

                {name:'Midnight Coffee', calories:[
                    {fat: 'Total fat 23g'},
                    {satured: 'Satured fat 13g'},
                    {trans: 'Trans fat 0.5g'}
                ],img:'coffee2.png',show:true},

                {name:'Green Coffee', calories:[
                    {fat: 'Total fat 23g'},
                    {satured: 'Satured fat 15g'},
                    {trans: 'Trans fat 0.2g'}
                ],img:'coffee3.png',show:true},

                {name:'Vanilla & Chocolate', calories:[
                    {fat: 'Total fat 43g'},
                    {satured: 'Satured fat 17g'},
                    {trans: 'Trans fat 0g'}
                ],img:'coffee4.png',show:false},

                {name:'Frapuccino', calories:[
                    {fat: 'Total fat 13g'},
                    {satured: 'Satured fat 9g'},
                    {trans: 'Trans fat 0g'}
                ],img:'coffee1.png',show:false},

                {name:'Midnight Coffee', calories:[
                    {fat: 'Total fat 23g'},
                    {satured: 'Satured fat 13g'},
                    {trans: 'Trans fat 0.5g'}
                ],img:'coffee2.png',show:false},

            ],
            actualIndex: null
        }
    },
    methods:{
        handleToggle(ev){
            this.actualIndex = ev
        },
        next(){
            this.productList.forEach(elem =>{
                if(elem.show == false){
                    elem.show = true
                }else{
                    elem.show = false
                }
            })
        },
        prev(){
            this.productList.forEach(elem =>{
                if(elem.show == true){
                    elem.show = false
                }else{
                    elem.show = true
                }
            })
        }
    },
    computed:{
        showed(){
            return this.productList.filter(elem => elem.show == true)
        }
    }
}
</script>

<style lang="scss">
@import '@/assets/_shared.scss';


.coffees{
    position: relative;
    width: 100%;
    padding: 100px 0;

    &--left, &--right{
        position: absolute;
        padding: 15px;
        top: 50%;
        bottom: 50%;
        z-index: 6;
        color: #fff;
        cursor: pointer;
        font-size: 2em;
        background-color: #000;
        border-radius: 50% 12%;
    }

    &--right{
        right: 15px;
    }

    &--left{
        left: 15px;
    }

    &__slider{
        display: flex;
        margin: 0 auto;
        width: 100%;
        gap: 80px;
        transition: transform 2s ease;
        justify-content: center;

    }

    &__card{
        display: grid;
        padding:50px;
        width: $card-width;
        margin-top:100px;
        grid-template-rows:200px 80px;
        background-color: $card-bgcolor;
        color: $card-fontcolor;
        justify-items: flex-start;
        border-radius: 45px;
        transition: all 1s ease;
        cursor: pointer;

        p{
            margin:5px
        }
    }

    &__milk, &__size{
        display: flex;
        justify-content: space-between;
        align-items: center;

        select{
        color: #fff;
        border: 0;
        border-bottom: 1px solid #fff;
        background-color: transparent;
        padding: 5px;
        height: fit-content;
        cursor: pointer;

        &:focus{
            outline: 0;
        }

        option{
            font-size: 1.5em;
            color: #000;
        }
        }
    }

    &__img{
        display: flex;
        width: 100%;
        padding: 10px;
        justify-content: center;
        img{
            margin-top:-170px ;
            width: 100%;
            object-fit: cover;
        }
    }

    &__selects{
        width: 100%;
    }

}

.actual{
        background-color: #448f79;
        transform: scale(1.2);
        color: #fff;
        z-index: 4;
        box-shadow: 25px 10px 51px 1px rgba(0,0,0,0.20);
        cursor: default;
}

.bigger{
    transform: scale(1.3);
}

</style>