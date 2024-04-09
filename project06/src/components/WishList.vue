<!-- WishList.vue -->
<template lang="html">
    <section>
        <transition-group name="list" tag="ul">
            <li v-for="(wishItem, index) in propsData" v-bind:key="wishItem" class="shadow">
                <i class="checkBtn fas fa-check" aria-hidden="true"></i>
                {{wishItem}}
                <span class="removeBtn" type="button" @click="removeWish(wishItem, index)">
                    <i class="far fa-trash-alt" aria-hidden="true"></i>
                </span>
            </li>
        </transition-group>
    </section>
</template>
<script>
    export default {
        props: ['propsData'],
        methods: {
            removeWish(wishItem, index){
                //localStorage.removeItem(wishItem);
                //this.wishItems.splice(index, 1); //인댁스를 지워라는 뜻, 1개씩
                this.$emit('removeWish', wishItem, index); //여기서 상위로 삭제할 내용을 전달하고 app.vue에서 실제로 삭제
            }
        }
    }
</script>
<style lang="css" scoped>
    .list-enter-active, .list-leave-active{transition: all 1s;}
    .list-enter, .list-leave-to{opacity:0; transform: translateY(30px);}
    ul{list-style-type:none; padding-left:0px; margin-top:0px; text-align:left;}
    li{display:flex; min-height:50px; height:50px; line-height:50px; margin:0.5em 0; padding: 0 0.9em; background: #fefefe; border-radius: 5px; overflow: hidden; text-overflow:ellipsis;}
    .checkBtn{line-height:50px; color:#ff8000; margin-right:5px;}
    .removeBtn{margin-left: auto; color:#de4343;}
</style>
