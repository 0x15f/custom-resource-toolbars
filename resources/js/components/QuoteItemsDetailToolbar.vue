<template>
    <div>
        <div class="flex w-full justify-end items-center">
           <a 
                title="Back to Quote"
                class="btn btn-default btn-icon  btn-white"
               :href="`/nova/resources/quotes/${this.parentResourceId}`">
                <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24"><path class="heroicon-ui" d="M5.41 11H21a1 1 0 0 1 0 2H5.41l5.3 5.3a1 1 0 0 1-1.42 1.4l-7-7a1 1 0 0 1 0-1.4l7-7a1 1 0 0 1 1.42 1.4L5.4 11z"/></svg>
             </a>
        </div>
    </div>
</template> 

<script>
    export default {
        props: ['resourceName', 'resourceId', 'field'],
        data() {
            return {
                parentResourceId: ''
            }
        },
        created() {
            this.fetch()
        },
        mounted() {
            var elements = document.getElementById('nova').querySelectorAll('h4');

            [].forEach.call(elements, function(element) {
                if(element.innerHTML === 'Custom Detail Toolbar') {
                    element.parentNode.remove();
                }
            });
        },
        methods: {
            fetch() {
                Nova.request().get(`/nova-vendor/custom-resource-toolbar/parent/${this.$parent.resourceId}`)
                .then(response => {
                    this.parentResourceId = response.data.id;
                });
            }
        }
    }
</script>