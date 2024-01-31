<template>
   <div class="discount">
    <h4>지금 결제하면 {{amount}}% 할인</h4>
   </div>
</template>

<script>
export default {
    name : 'DiscountItem',

    data(){
        return {
            amount : 50,
        }
            },
            methods : {

            },
            mounted(){
                setInterval(()=>{
                    this.amount--
                },1000)
            }
    }
</script>

<style>

</style>

