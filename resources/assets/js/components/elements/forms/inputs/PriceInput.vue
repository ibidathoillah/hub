<template>
    <div>
        <currency-data>
            <div class="input-group input-group-full" slot-scope="currency">
                <span class="input-group-addon" v-html="currency.symbol"></span>
                <input type="number" class="form-control" v-model="price" step="0.01">
                <span class="input-group-addon">Excl. Tax</span>
            </div>
        </currency-data>
    </div>
</template>

<script>
    import CurrencyData from '../../../elements/CurrencyConverter.vue';

    export default {
        components: {
            CurrencyData
        },
        props: {
            value: {
                required: true,
                type: [String, Number]
            },
            tax: {
                required: false,
                type: Object
            }
        },
        computed: {
            price : {
                get: function() {
                    return this.value;
                },
                set: function (val) {
                    this.$emit('input', val);
                }
            }
        }
    }
</script>