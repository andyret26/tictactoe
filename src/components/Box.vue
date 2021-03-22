<template>
    <div class="box" @click.self="test()">
        {{msg}}
    </div>
    
</template>

<script>
export default {
    name:'Box',
    props: {
        boxNum: {
            type: Number,
            required: true
        },

        round: Number
    },

    data: function(){
        return{
            msg: '',
            title: 'FORM CHILD TO PARENT'
        }
    },

    methods: {
        test: function(){
            

            if(this.round % 2 === 0){
                this.msg = 'X'
            }
            else{
                this.msg = 'O'
            }


            this.$emit('boxClicked', this.boxNum)
        }
    }
}
</script>

<style scoped>

    .box{
        font-size: 4em;
    }

</style>