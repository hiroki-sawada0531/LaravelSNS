<template>
    <div>
        <button type="button" class="btn m-0 p-1 shadow-none">
            <i class="fas fa-heart mr-1"
            :class="{'red-text':this.isLikedBy}"
            @click="clickLike"
            >
            </i>
        </button>
        {{ countLikes }}
    </div>
</template>

<script>
export default {
    methods: {
        clickLike() {
            if (!this.authorized) {
                alert('いいね機能はログイン中のみ使用できます')
                return
            }

            this.isLikedBy
            ? this.unlike()
            :this.like()
        },
    },
    props: {
        initialIsLikedBy: {
            type:Boolean,
            default:false,
        },
        initialCountLikes: {
            type:Number,
            default:0,
        },
        authorized: {
            type:Boolean,
            default:false,
        },
        endpoint: {
            type:String,
        },
    },
    data() {
        return {
            isLikedBy: this.initialIsLikedBy,
            countLikes: this.initialCountLikes,
        }
    },
}
</script>