<template>
  <header class="header">
    <div class="header__first">
        <img src="../assets/vuebucks logo.png" alt=""/>
        <p>COFFEE</p>
        <p>TEA</p>
        <p>MENU</p>
    </div>
    <div class="header__second">
        <input type="text" placeholder="SEARCH"/>
        <fa icon="search"/>
    </div>
    <div class="header__third">
        <fa icon='shopping-bag'/>
    </div>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss">

.header{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    grid-template-rows: 80px;
    padding: 50px 110px;

    &__first, &__second, &__third{
        display: flex;
        align-items: center;
        gap: 50px;
        
        p{
            cursor: pointer;
            padding: 15px;
            transition: all .1s ease-out;

            &:hover{
                background-color: rgba(0, 0, 0, 0.082);
                border-radius: 10px;
            }

            &:active{
                transform: scale(.9);
            }
        }

        img{
            cursor: pointer;
            width: 100px;
            height: 100px;
        }
    }

    &__third{
        justify-content: flex-end;
        svg{
            font-size:2em;
        }
    }

    &__second{
        justify-content: flex-end;

        input{
            position: relative;
            width: 75%;
            border: none;
            border-bottom: 1px solid rgba(0, 0, 0, 0.514);
            padding: 10px;
            padding-left: 5px;
            background-color: transparent;

            &:focus{
                outline: none;
            }
        }

        svg{
            position: absolute;
        }
    }
}

</style>