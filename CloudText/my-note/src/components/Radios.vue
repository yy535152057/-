<template>
    <div class="radios clearfix">
        <label class="radios-label fl" v-for="item in options">
            <input type="radio" v-model="currentValue" class="radios-item" :value="item._id">
            <div class="radios-wrap">
                <span class="radios-title">{{item.name}}</span>
            </div>
        </label>
    </div>
</template>

<script>
    export default {
        props: {
            options: {
                type: Array
            },
            value: String
        },
        data() {
            return {
                currentValue: this.value
            }
        },
        watch: {
            value(val) {
                this.currentValue = val
            },
            currentValue(val) {
                this.$emit('input', val)
                this.$emit('change', val)
            }
        }
    }
</script>

<style scoped lang="scss">
.radios-item{
    display: none;
}
.radios-wrap{
    padding: 10px 15px;
    font-size: 14px;
    font-weight: 400;
    color: #444;
    border: 1px solid #f1f1f1;
    border-radius: 4px;
    margin-right: 20px;
}
.radios-item:checked + .radios-wrap{
    color: #fff;
    background: #409eff;
}



</style>