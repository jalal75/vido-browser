<template>
    <div>
        Search Bar:
        <input @input="onInput" />
    </div>
</template>

<script>
export default {
    name: "SeachBar",
    methods:{
        onInput: function(e){
            this.$emit('termChange', e.target.value);
            
        }
    }
}
</script>

<style scoped>
    input{
        width: 75%
    }
    div{
        text-align: center;
        margin: 20px;
    }
</style>
