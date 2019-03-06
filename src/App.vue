<template>
    <div id="app">
        <router-view/>
    </div>
</template>

<style lang="scss">
    @import "components/mixins";

    body {
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
        font-size: 12px;
    }

    * {
        -webkit-box-sizing: border-box;
        box-sizing: border-box;
    }

    .section-container {
        width: 210mm;
        height: 297mm;
        padding: 20mm;
        margin: 10mm auto;
        border: 1px #D3D3D3 solid;
        background: white;
    }

    .blocks {
        /*padding: 1cm;*/
        height: 257mm;
        margin: 0;
    }

    @page {
        size: A4;
        margin: 0;
    }

    @media print {
        html, body {
            width: 210mm;
            height: 297mm;
        }
        .blocks {
            margin: 0;
            border: initial;
            border-radius: initial;
            width: initial;
            min-height: initial;
            box-shadow: initial;
            background: initial;
            page-break-after: always;
        }
    }

    #app {
        font-family: "Arial", Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        color: $black;
        text-align: left;
    }

    #nav {
        padding: 30px;

        a {
            font-weight: bold;
            color: $black;

            &.router-link-exact-active {
                color: #42b983;
            }
        }
    }
</style>
