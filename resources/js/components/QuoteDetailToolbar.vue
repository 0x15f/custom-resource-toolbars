<template>
    <div>
        <div class="flex w-full justify-end items-center">
           <a
                class="btn btn-default btn-icon btn-white"
                :href="'/nova-vendor/custom-resource-toolbar/export-quote/' + this.$parent.resourceId"
                style="background-color: var(--primary); color: white;">
                Export as PDF
             </a>
        </div>
    </div>
</template> 

<script>
    export default {
        props: ['resourceName', 'resourceId', 'field'],
        mounted() {
            var elements = document.getElementById('nova').querySelectorAll('h4');

            [].forEach.call(elements, function(element) {
                if(element.innerHTML === 'Custom Detail Toolbar') {
                    element.parentNode.remove();
                }
            });
        }
    }
</script>