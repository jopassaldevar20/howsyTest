<template>
    <div class="post_card_wrapper">
        <div class="pc__thumb_container">
            <div
                class="tc__image_container"
                :style="{ backgroundImage: 'url(' + url + ')' }"
                @click="expandPost(index)"
            ></div>
            <div class="tc__thumb_info">
                <div class="ti__info_container">
                    <span class="icon-eye"></span>
                    <p>{{ eye }}</p>
                </div>
                <div class="ti__info_container">
                    <span class="icon-comment"></span>
                    <p>{{ comments }}</p>
                </div>
                <div class="ti__info_container">
                    <span class="icon-heart"></span>
                    <p>{{ hearts }}</p>
                </div>
            </div>
        </div>
        <div class="pc__author_container">
            <div
                class="ac__image_container"
                :style="{ backgroundImage: 'url(' + thumbnailUrl + ')' }"
            ></div>
            <p>{{ title }}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PostCard',
    props: {
        index: {
            type: Number,
            required: true
        },
        url: {
            type: String,
            required: true
        },
        eye: {
            type: Number,
            required: true
        },
        comments: {
            type: Number,
            required: true
        },
        hearts: {
            type: Number,
            required: true
        },
        thumbnailUrl: {
            type: String,
            required: true
        },
        title: {
            type: String,
            required: true
        }
    },
    methods: {
        expandPost (index) {
            this.$emit('expand', index);
        }
    }
};
</script>

<style scoped lang="scss">
    .post_card_wrapper {
        margin: 20px;

        .pc__thumb_container {
            width: 250px;
            height: 250px;
            padding-top: 10px;
            display: flex;
            flex-direction: column;
            background-color: #fff;

            .tc__image_container {
                width: 90%;
                height: 80%;
                margin: 0 auto;
                background-color: #ccc;
                background-image: url('../assets/placeholder.jpg');
                background-position: center center;
                background-size: cover;
                cursor: pointer;
            }

            .tc__thumb_info {
                width: 90%;
                margin: 0 auto;
                display: flex;
                align-items: center;
                flex-grow: 1;
                justify-content: flex-end;

                .ti__info_container {
                    margin-left: 10px;
                    color: #a1a1a1;
                    display: flex;
                    align-items: center;

                    > span {
                        font-size: 16px;
                    }

                    > p {
                        margin-left: 4px;
                        font-size: 14px;
                    }
                }
            }
        }

        .pc__author_container {
            width: 250px;
            margin-top: 10px;
            margin-left: 10px;
            display: flex;
            align-items: flex-start;

            .ac__image_container {
                width: 25px;
                height: 25px;
                flex-shrink: 0;
                background-image: url('../assets/placeholder.jpg');
                background-position: center center;
                background-size: 100%;
                border-radius: 50%;
                overflow: hidden;
            }

            > p {
                margin-left: 8px;
                color: #5794bb;
                font-size: 16px;
                text-align: left;
            }
        }
    }
</style>
