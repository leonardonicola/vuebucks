<template>
  <header class="header">
    <div class="header__first">
        <img src="../assets/vuebucks logo.png" alt=""/>
        <div class="header__first--mobile">
            <p>COFFEE</p>
            <p>TEA</p>
            <p>MENU</p>
        </div>
    </div>
    <div class="header__second">
        <input type="text" placeholder="SEARCH"/>
        <fa icon="search"/>
    </div>
  </header>
</template>

<script>
export default {

}
</script>

<style lang="scss">

.header{
    display: flex;
    justify-content: space-between;
    padding: 50px 110px;

    &__first, &__second{
        display: flex;
        align-items: center;
        gap: 50px;
        width: 100%;
        
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

        &--mobile{
            display: flex;
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

@media screen and (max-width:950px) {
    .header{
        justify-items: center;

        &__second{
        display: none;
        }
    }
}

@media screen and (max-width:600px) {
    .header__first{
        justify-content: center;
        &--mobile{
            display: none;
        }
    }
}



</style>