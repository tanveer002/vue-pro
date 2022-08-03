<template>
    <p>Reaction Time For Game is {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
    export default{
        props : ['score'],
        data(){
            return{
                rank : null
            }
        },
        mounted(){
            if (this.score < 2250) {
                this.rank = 'Nija Figure'
            }
            else if (this.score < 2400) {
                this.rank = 'Rapid Reflex'
            } else {
                this.rank = 'Sanil Pace...'
            }
        }
}
</script>

<style>
    .rank{
        font-size: 1.4rem;
        color: #0faf87;
        font-weight: bold;
    }
</style>