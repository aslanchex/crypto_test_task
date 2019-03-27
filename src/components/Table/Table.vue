<script>
export default {
    props: ['assets']
}
</script>


<template>
    <div :class="$style.container">
        <table :class="$style.table">
            <thead :class="$style.table__header">
                <tr :class="$style.table__row">
                    <th :class="$style.table__head">Название</th>
                    <th :class="$style.table__head">Стоимость</th>
                    <th :class="[$style.table__head, $style.table__cap]">Рыночная капитализация</th>
                    <th :class="[$style.table__head, $style.table__vwap]">Суточный объем</th>
                </tr>
            </thead>
        <tbody :class="$style.table__body">
            <div :class="$style['table__body-inner']">
                <tr :class="$style.table__row" v-for="asset in assets" :key="asset.id">
                    <td data-label="Название" :class="$style.table__cell">{{asset.name}}</td>
                    <td data-label="Стоимость" :class="$style.table__cell">{{(asset.priceUsd)}}</td>
                    <td data-label="Рыночная капитализация" :class="[$style.table__cell, $style.table__cap]">${{Math.ceil(asset.marketCapUsd)}}</td>
                    <td data-label="Суточный объем" :class="[$style.table__cell, $style.table__vwap]">${{Math.ceil(asset.volumeUsd24Hr)}}</td>
                </tr>
            </div>
        </tbody>
        </table>
    </div>
</template>

<style lang="scss" module>
$black: #222222;
$white: #ffffff;
$accent: #fafafa;

.container {
    height: 10em;
}
.table {
    margin: 20px auto;
    display: flex;
    flex-flow: column;
    width: 90%;  
    height: 530px;
    box-shadow: 0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
    
    &__header {
        display: table;
        flex: 0 0 auto;
        width: 100%;
        table-layout: fixed;
        background: #0099FF;
        color: $white;
    }

    &__body {
        display: block;
        flex: 1 1 auto;
        overflow: hidden;
        &:hover, &:active {
            overflow-y: scroll;
        }
    }

    &__body-inner {
        width: 90vw;
    }

    &__row {
        display: table;
        width: 100%;
        table-layout: fixed;
        &:nth-child(2n) {
            background: $accent;
        }
    }   

    &__head,
    &__cell {
        padding: 1em;
    }

    &__cell {
        text-align: center;
    }
}

@media screen and (max-width: 715px) {
  .table {
    border: 0;

    &__body-inner {
        width: 90vw;
    }
    
    &__cap,
    &__vwap {
        display: none;
    }
  }
}

@media screen and (max-width : 450px) {
    .table {
        &__cell {
            font-size: 13px;
            word-wrap: break-word;
        }
    }
}
</style>
