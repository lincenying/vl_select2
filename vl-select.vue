<template>

<select v-el:select :multiple="multiple" class="js-example-basic-single">

</select>

</template>

<script>
import select2 from "select2";
export default {
    props: {
        model: {
            required: true,
            twoWay: true
        },
        data: {
            required: true,
            type: Array
        },
        ajax: {
            required: false,
            type: Object
        },
        tags: {
            required: false,
            default: true
        },
        multiple: {
            required: false,
            default: false
        },
        allowclear: {
            required: false,
            default: true
        },
        placeholder: {
            required: false,
            type: String
        },
        escapemarkup: {
            required: false
        },
        templateselection: {
            required: false
        },
        templateresult: {
            required: false
        }
    },
    ready() {
        let config = {
            placeholder: this.placeholder,
            allowClear: this.allowClear || false,
        };
        if (this.ajax.url) {
            config.ajax = this.ajax;
            config.minimumInputLength = 1;
            config.escapeMarkup = this.escapemarkup;
            config.templateSelection = this.templateselection;
            config.templateResult = this.templateresult;
        } else {
            config.data = this.data;
        }
        if (this.multiple) {
            config.tags = true;
        } else {
            config.tags = this.tags;
        }
        this.$els.select = $(this.$els.select).select2(config).val(this.model).trigger('change')
        .on('change', (e)=>{
            this.model = this.$els.select.val()
        });
    },
    detached() {
        this.$els.select.off('select2:unselecting')
    }
};
</script>
