<template>
    <div class="section-container">
        <form class="blocks">
            <div class="title-wrapper">
                <p class="name"><b>Name, Vorname:</b>
                    <input type="text" id="text-name" class="title-detail name-box">
                </p>
                <p class="ausbildungnachweis"><b>Ausbildungsnachweis</b>
                    <label class="regular-texts">Nr.</label>
                    <input type="text" id="text-ausnr"
                           class="title-detail ausbildung-box">
                    <label class="regular-texts">für die Woche vom</label>
                    <date-picker v-model="time1" lang="en" :not-before="new Date()" format="DD.MM.YYYY"
                                 width="130px"></date-picker>
                    <label class="regular-texts">bis</label>
                    <date-picker v-model="time2" lang="en" :not-before="new Date()" format="DD.MM.YYYY"
                                 width="130px"></date-picker>
                </p>
                <p class="abteilung">Abteilung oder Arbeitsgebiet:
                    <!--<input type="text" id="text-abteilung" class="title-detail abteilung-box">-->
                    <select autofocus name="bildungbereich" id="text-abteilung" class="title-detail abteilung-box">
                        <option value="Anwendungsentwicklung">Fachinformatiker für Anwendungsentwicklung</option>
                        <option value="Systemintegration">Fachinformatiker für Systemintegration</option>
                        <option value="Systementwicklung" selected>Programmierung und Systementwicklung</option>
                    </select>
                    <label class="regular-texts">Ausbildungsjahr:</label>
                    <!--<input type="text" id="text-zeit" class="title-detail ausjahr-box">-->
                    <select autofocus name="jahres" id="text-zeit" class="title-detail ausjahr-box">
                        <option value="1" selected>1</option>
                        <option value="2">2</option>
                        <option value="3">3</option>
                    </select>
                </p>
            </div>
            <div class="tatigkeit-wrapper">
                <h3>Betriebliche Tätigkeit</h3>
                <div id="text-tatigkeit" class="tatigkeit-detail" contenteditable>
                </div>
            </div>
            <div class="sonstige-wrapper">
                <h3>Unterweisungen, betrieblicher Unterricht, sonstige Schulungen</h3>
                <div id="text-sonstige" class="sonstige-detail" contenteditable></div>
            </div>
            <div class="schule-wrapper" id="schule-input">
                <h3>Berufsschule (Unterrichtsthemen)</h3>
                <div id="text-schule" class="schule-detail" contenteditable>
                </div>
                ****autocomplete.php must be done here
            </div>
            <div class="sign-wrapper">
                <div class="sign-left signed">
                    <p>Datum:
                        <date-picker v-model="time3" lang="en" :not-before="new Date()"
                                     format="DD.MM.YYYY" width="130px"></date-picker>
                    </p>
                    <p class="sign">
                        Unterschrift Auszubildender
                    </p>
                </div>
                <div class="sign-right signed">
                    <p>Datum:
                        <date-picker v-model="time4" lang="en" :not-before="new Date()"
                                     format="DD.MM.YYYY" width="130px"></date-picker>
                    </p>
                    <p class="sign">
                        Unterschrift Ausbildender
                    </p>
                </div>
            </div>
        </form>
    </div>
</template>

<script>
    import DatePicker from 'vue2-datepicker'
    import $ from 'jquery';

    export default {
        name: "Body",
        components: {
            DatePicker,
            $,
        },
        data() {
            return {
                time1: '',
                time2: '',
                time3: '',
                time4: '',
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
        @include font-bold();
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
                border-bottom: 1px solid $black;

                .name {
                    .name-box {
                        width: 350px;
                    }
                }

                .ausbildungnachweis {
                    .ausbildung-box {
                        text-align: center;
                        width: 60px;
                    }

                    .regular-texts {
                        @include regular-text();
                        margin: 10px;
                    }
                }

                .abteilung {
                    @include font-regular();

                    .abteilung-box {
                        width: 290px;
                    }

                    .regular-texts {
                        @include regular-text();
                        margin: 10px;
                    }

                    .ausjahr-box {
                        text-align: center;
                        width: 25px;
                    }
                }

                .title-detail {
                    @include input-text();
                    margin-left: 2px;
                }
            }

            .tatigkeit-wrapper {
                @include blocks();

                h3 {
                    border-bottom: 1px solid $black;
                    padding: 2px 0 2px 5px;
                    margin: 0 auto;
                }

                .tatigkeit-detail {
                    @include input-text();
                    @include block-size();
                }
            }

            .sonstige-wrapper {
                @include blocks();

                h3 {
                    border-bottom: 1px solid $black;
                    padding: 2px 0 2px 5px;
                    margin: 0 auto;
                }

                .sonstige-detail {
                    @include input-text();
                    @include block-size();
                }
            }

            .schule-wrapper {
                @include blocks();

                h3 {
                    border-bottom: 1px solid $black;
                    padding: 2px 0 2px 5px;
                    margin: 0 auto;
                }

                .schule-detail {
                    @include input-text();
                    @include block-size();
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
                    width: 90%;
                    border-top: 1px solid $black;
                }

                .sign-left {
                    width: 45%;
                }

                .sign-right {
                    position: relative;
                    width: 50%;
                    border-left: 1px solid $black;
                }
            }
        }
    }
</style>
