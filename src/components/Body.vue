<template>
    <div class="section-container">
        <section class="blocks">
            <div class="title-wrapper">
                <p class="title">{{ name }}</p> <textarea name="self-add" id="text-input" cols="1" rows="1"
                                                class="detail"></textarea>
            </div>
        </section>
    </div>
</template>

<script>
    export default {
        name: "Body",
        props: {
            msg: String
        }
    };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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

    a {
        color: #42b983;
    }
</style>
