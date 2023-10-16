<template>
    <div class="page">
        <h4>Thêm Liên hệ</h4>
        <ContactForm
            :contact="contact"
            @submit:contact="addContact"
           
        />
        <p>{{ message }}</p>
    </div>
</template>

<script>
    import ContactForm from "@/components/ContactForm.vue";
    import ContactService from "@/services/contact.service";
    export default {
        components: {
            ContactForm,
           
        },
        props: {
            //id: { type: String, required: true },
        },
        data() {
            return {
                contact: null,
                message: "",
            };
        },
        methods: {

            async addContact(data) {
                try {
                
                    await ContactService.create(data);
                    this.message = "Liên hệ thêm thành công.";
                   
                } catch (error) {
                    console.log("chay add contact catch")
                    console.log(error);
            }
            },
            
        },
        created() {
            this.contact = [];
            this.message = "";
        },
        
    };
</script>