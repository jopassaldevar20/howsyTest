<template>
    <div class="the_modal_wrapper">
        <span
            class="tm__icon icon-cancel"
            @click="closeModal"
        ></span>
        <div class="tm__body_content">
            <img :src="url" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'TheModal',
    props: {
        url: {
            type: String,
            required: true
        }
    },
    methods: {
        closeModal () {
            this.$emit('collapse');
        }
    }
};
</script>

<style scoped lang="scss">
    .the_modal_wrapper {
        width: 100%;
        height: 100%;
        position: fixed;
        top: 0;
        left: 0;
        background-color: rgba(0, 0, 0, .5);

        .tm__icon {
            position: absolute;
            top: 10px;
            right: 10px;
            color: #fff;
            font-size: 50px;
            cursor: pointer;
        }

        .tm__body_content {
            margin: 200px auto 0;

            > img {
                max-width: 800px;
            }
        }
    }
</style>
