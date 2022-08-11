<template>
<div class="coffees">

    <VueSlickCarousel class="slider" v-bind="settings">
        
        <div v-for="(coffee, i) in productList" :key="i"
        class="coffees__card"
        ref="card"
        @click="handleToggle(i)"
        :class="actualIndex == i ? 'actual':''">

            <div class="coffees__img">
                <img :src="require(`../assets/${coffee.img}`)" loading="lazy" alt="Coffee :)"
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
                    <select name="size">
                        <option value="demi">Demi</option>
                        <option value="short">Short</option>
                        <option value="Tall">Tall</option>
                        <option value="Grande">Grande</option>
                        <option value="Venti">Venti</option>
                    </select>
                </div>

                <div class="coffees__milk">
                    <h2>Milk</h2>
                    <select name="milk">
                        <option value="cremoso">Cremoso</option>
                        <option value="aveia">Aveia</option>
                        <option value="vegetal">Vegetal</option>
                    </select>
                </div>
            </div>
        </div>
    </VueSlickCarousel>
</div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
// optional style for arrows & dots
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'
export default {
components: { VueSlickCarousel },

data(){
    return{
        settings:{
        "dots": true,
        "infinite": false,
        "speed": 500,
        "slidesToShow": 3,
        "slidesToScroll": 3,
        "initialSlide": 0,
        "responsive": [
            {
            "breakpoint": 1300,
            "settings": {
                "slidesToShow": 2,
                "slidesToScroll": 2,
                "infinite": true,
                "dots": true
            }
            },
            {
            "breakpoint": 1000,
            "settings": {
                "slidesToShow": 1,
                "slidesToScroll": 1,
                "initialSlide": 2
            }
            }
        ]
        },
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
                {fat: 'Total fat 3g'},
                {satured: 'Satured fat 0g'},
                {trans: 'Trans fat 0g'}
            ],img:'coffee3.png'},

            {name:'Vanilla & Chocolate', calories:[
                {fat: 'Total fat 43g'},
                {satured: 'Satured fat 17g'},
                {trans: 'Trans fat 0g'}
            ],img:'coffee4.png'},

            {name:'Banana Shake', calories:[
                {fat: 'Total fat 10g'},
                {satured: 'Satured fat 4g'},
                {trans: 'Trans fat 0g'}
            ],img:'coffee5.png'},

            {name:'Midnight Coffee', calories:[
                {fat: 'Total fat 23g'},
                {satured: 'Satured fat 13g'},
                {trans: 'Trans fat 0.5g'}
            ],img:'coffee2.png'},

        ],
        actualIndex: null
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

.slider{
    
    margin: 0 100px;

    button{
        transform: scale(2);
    }

    .slick-prev::before, .slick-next::before{
        color: #000;
    }

    .slick-next{
        right: -45px;
    }

    .slick-prev{
        left: -45px;
    }

    .coffees{
    position: relative;
    width: 100%;
    padding: 100px 0;

        &__card{
            display: grid !important;
            width: $card-width !important;
            padding:50px;
            margin:100px auto;
            grid-template-rows:200px 80px;
            background-color: $card-bgcolor;
            color: $card-fontcolor;
            border-radius: 45px;
            transition: all 1s ease;
            cursor: pointer;

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
                    color: #000;
                }
            }
        }

        &__img{
            display: flex;
            width: 100%;
            padding: 10px;
            img{
                margin-top:-170px ;
                width: 100%;
                object-fit: cover;
                user-select: none;
                pointer-events: none;
            }
        }

        &__selects{
            width: 100%;
        }

    }

    .actual{
        background-color: #448f79;
        color: #fff;
        z-index: 4;
        cursor: default;
    }

    .bigger{
        transform: scale(1.3);
    }
}


</style>