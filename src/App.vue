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
        -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
        box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
    }

    .blocks {
        height: 257mm;
        margin: 0;
    }

    @page {
        size: A4;
        margin: 0;
    }

    @media print {
        html, body {
            font-family: Arial;
            width: 210mm;
            max-height: 297mm;
        }

        .mx-input {
            height: 28px !important;
            font-size: 12px !important;
            color: $black !important;
            border-radius: 0px !important;
            background-color: $white !important;
            border: 1px solid $black !important;
            margin-left: 2px !important;
            box-shadow: none !important;

            &-append {
                display: none;
            }
        }

        .section-container {
            margin-top: -1px;
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
