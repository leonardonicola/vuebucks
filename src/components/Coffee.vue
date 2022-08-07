<template>
<div class="coffees" @click.self="actualIndex = null">
    <div v-for="(coffee, i) in productList" :key="i" class="coffees__card"
    @click="handleToggle(i)"
    :class="actualIndex == i ? 'actual':''">
        <div class="coffees__img">
            <img :src="require(`../assets/${coffee.img}`)" alt="Coffee :)"
            :style="i == 1? 'margin-bottom:-35px; transform:scale(0.85)':''"
            :class="i == 3 ? 'bigger':''">
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
                ],img:'coffee1.png'},

                {name:'Midnight Coffee', calories:[
                    {fat: 'Total fat 23g'},
                    {satured: 'Satured fat 13g'},
                    {trans: 'Trans fat 0.5g'}
                ],img:'coffee2.png'},

                {name:'Green Coffee', calories:[
                    {fat: 'Total fat 23g'},
                    {satured: 'Satured fat 15g'},
                    {trans: 'Trans fat 0.2g'}
                ],img:'coffee3.png'},

                {name:'Vanilla & Chocolate', calories:[
                    {fat: 'Total fat 43g'},
                    {satured: 'Satured fat 17g'},
                    {trans: 'Trans fat 0g'}
                ],img:'coffee4.png'}

            ],
            actualIndex:null
        }
    },
    methods:{
        handleToggle(ev){
            this.actualIndex = ev
        }
    }
}
</script>

<style lang="scss">
@import '@/assets/_shared.scss';

.bigger{
    transform: scale(1.3);
}

.coffees{
    display: grid;
    justify-content: space-evenly;
    grid-template-columns: repeat(auto-fit, 350px);
    justify-items: center;
    margin: 30px 0 80px 0;
    padding: 20px;
    gap: 10px;

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

    &__selects{
        width: 100%;
    }

    &__card{
        display: grid;
        padding:50px;
        width: 100%;
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

    .actual{
        background-color: #448f79;
        transform: scale(1.2);
        color: #fff;
        z-index: 4;
        box-shadow: 25px 10px 51px 1px rgba(0,0,0,0.20);
        cursor: default;
    }

}
</style>