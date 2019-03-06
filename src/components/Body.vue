<template>
    <div class="section-container">
        <section class="blocks">
            <div class="title-wrapper">
                <p class="name"><b>Name, Vorname:</b> <input type="text" id="text-name" class="title-detail name-box">
                </p>
                <p class="ausbildungnachweis"><b>Ausbildungsnachweis</b> Nr. <input type="text" id="text-ausnr"
                                                                                    class="title-detail ausbildung-box">
                    für die Woche vom
                    <date-picker v-model="time1" lang="en" :not-before="new Date()" format="DD.MM.YYYY"
                                 width="130px"></date-picker>
                    bis
                    <date-picker v-model="time1" lang="en" :not-before="new Date()" format="DD.MM.YYYY"
                                 width="130px"></date-picker>
                </p>
                <p class="abteilung">Abteilung oder Arbeitsgebiet:
                    <!--<input type="text" id="text-abteilung" class="title-detail abteilung-box">-->
                    <select autofocus name="bildungbereich" id="text-abteilung" class="title-detail abteilung-box">
                        <option value="Anwendungsentwicklung">Fachinformatiker für Anwendungsentwicklung</option>
                        <option value="Systemintegration">Fachinformatiker für Systemintegration</option>
                        <option value="Systementwicklung" selected>Programmierung und Systementwicklung</option>
                    </select>
                    Ausbildungsjahr:
                    <!--<input type="text" id="text-zeit" class="title-detail ausjahr-box">-->
                    <select autofocus name="jahres" id="text-zeit" class="title-detail ausjahr-box">
                        <option value="1" selected>1</option>
                        <option value="2">2</option>
                        <option value="3">3</option>
                        <option value="4">4</option>
                    </select>
                </p>
            </div>
            <div class="tatigkeit-wrapper">
                <p>Betriebliche Tätigkeit</p>
                <div id="text-tatigkeit" class="tatigkeit-detail" contenteditable>
                </div>
            </div>
            <div class="sonstige-wrapper">
                <p>Unterweisungen, betrieblicher Unterricht, sonstige Schulungen</p>
                <div id="text-sonstige" class="sonstige-detail" contenteditable></div>
            </div>
            <div class="schule-wrapper" id="schule-input">
                <p>Berufsschule (Unterrrichtsthemen)</p>
                <div id="text-schule" class="schule-detail" contenteditable>
                </div>
                ****autocomplete.php must be done here
            </div>
            <div class="sign-wrapper">
                <div class="sign-left signed">
                    <p>Datum:
                        <date-picker v-model="time1" lang="en" :not-before="new Date()"
                                     format="DD.MM.YYYY" width="130px"></date-picker>
                    </p>
                    <p class="sign">
                        Unterschrift Auszubildender
                    </p>
                </div>
                <div class="sign-right signed">
                    <p>Datum:
                        <date-picker v-model="time1" lang="en" :not-before="new Date()"
                                     format="DD.MM.YYYY" width="130px"></date-picker>
                    </p>
                    <p class="sign">
                        Unterschrift Ausbildender
                    </p>
                </div>
            </div>
        </section>
    </div>
</template>

<script>
    import DatePicker from 'vue2-datepicker'
    import $ from 'jquery';
    import fitty from 'fitty';

    export default {
        name: "Body",
        components: {
            DatePicker,
        },
        data() {
            return {
                time1: '',
                time2: '',
                time3: '',
                // custom lang
                lang: {
                    days: ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'],
                    months: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
                    pickers: ['next 7 days', 'next 30 days', 'previous 7 days', 'previous 30 days'],
                    placeholder: {
                        date: 'Select Date',
                        dateRange: 'Select Date Range'
                    }
                },
                // custom range shortcuts
                shortcuts: [
                    {
                        text: 'Today',
                        onClick: () => {
                            this.time3 = [new Date(), new Date()]
                        }
                    }
                ],
                timePickerOptions: {
                    start: '00:00',
                    step: '00:30',
                    end: '23:30'
                }
            }
        },
        mounted() {
            this.adaptHeight();
        },
        methods: {
            adaptHeight() {
                fitty('#text-schule', {
                    minSize: 14,
                    maxSize: 72,
                    multiLine: true,
                });
            }
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    @import "mixins";


    h3 {
        margin: 40px 0 0;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }

    li {
        display: inline-block;
        margin: 0 10px;
    }

    p {
        b {
            font-size: 14px;
        }

        font-size: 12px;
        margin: 2px;
    }

    input {
        font-size: 18px;
        font-weight: 500;
    }

    select {
        -webkit-appearance: none;
        -moz-appearance: none;
        appearance: none;
        padding: 2px 30px 2px 2px;
    }

    .section-container {

        .blocks {
            .title-wrapper {
                @include blocks();

                .name {
                    .name-box {
                        width: 350px;
                    }
                }

                .ausbildungnachweis {
                    .ausbildung-box {
                        text-align: center;
                        width: 40px;
                    }
                }

                .abteilung {
                    .abteilung-box {
                        width: 290px;
                    }

                    .ausjahr-box {
                        text-align: center;
                        width: 40px;
                    }
                }

                .title-detail {
                    @include input-text();
                    margin-left: 2px;
                }
            }

            .tatigkeit-wrapper {
                @include blocks();

                .tatigkeit-detail {
                    @include input-blocks();
                }
            }

            .sonstige-wrapper {
                @include blocks();

                .sonstige-detail {
                    @include input-blocks();
                }
            }

            .schule-wrapper {
                @include blocks();

                .schule-detail {
                    width: 100%;
                    height: 228px;
                    $color: $black;
                    border: 1px solid $color;
                }
            }

            .sign-wrapper {
                @include blocks();
                position: relative;
                display: flex;
                justify-content: start;
                border: 1px solid $black;
                height: auto;

                .signed {
                    position: relative;
                    max-width: 100%;
                    text-align: left;
                }

                .sign {
                    margin-top: 60px;
                    position: relative;
                    width: 100%;

                    &::before {
                        position: absolute;
                        content: "";
                        background-color: $black;
                        width: 95%;
                        top: 0px;
                        height: 1px;
                    }
                }

                .sign-left {
                    width: 45%;
                }

                .sign-right {
                    position: relative;
                    width: 50%;

                    &::before {
                        content: "";
                        background-color: $black;
                        display: block;
                        width: 1px;
                        left: -4px;
                        height: 100%;
                        position: absolute;
                        top: 0;
                    }
                }
            }
        }
    }
</style>
