<template>
    <div>
        <select
            :class="selectClass"
            :id="selectId"
            @input="updateValue($event.target.value)"
            @change="handler()"
        >
            <option value="latest" :selected="value == 'latest'">Latest</option>
            <option value="price_asc" :selected="value == 'price_asc'">Price (Low &#8594; High)</option>
            <option value="price_desc" :selected="value == 'price_desc'">Price (High &#8594; Low)</option>
            <option value="name_asc" :selected="value == 'name_asc'">Name (A &#8594; Z)</option>
            <option value="name_desc" :selected="value == 'name_desc'">Name (Z &#8594; A)</option>
        </select>
    </div>
</template>
<script>
export default {
    props: {
        selectClass: {
            type: String
        },
        selectId: {
            type: String
        },
        value: {
            type: String,
            default: "latest"
        },
        changeHandler: {
            type: Function,
            default: ()=>{}
        }
    },
    methods: {
        updateValue: function(value) {
            this.$emit("input", value);
        },
        handler() {
            this.changeHandler();
        }
    }
};
</script>