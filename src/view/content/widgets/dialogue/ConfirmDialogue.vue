<template>
    <popup-modal ref="popup">
        <h2 style="margin-top: 0">{{ title }}</h2>
        <div class="d-block">
            <p>{{ message }}</p>
        </div>
        <div class="float-right">
            <span class="mr-5 btn" @click="_cancel">{{ cancelButton }}</span>
            <v-btn
                large
                color="primary"
                @click="_confirm">{{ okButton }}</v-btn>
        </div>
    </popup-modal>
</template>
<script>
    import PopupModal from '@/view/content/widgets/dialogue/PopupModal.vue'
    export default {
        name: 'ConfirmDialogue',
        components: { PopupModal },
        data: () => ({
            // Parameters that change depending on the type of dialogue
            title: undefined,
            message: undefined, // Main text content
            okButton: undefined, // Text for confirm button; leave it empty because we don't know what we're using it for
            cancelButton: 'Cancel', // text for cancel button
            
            // Private variables
            resolvePromise: undefined,
            rejectPromise: undefined,
        }),

    methods: {
        show(opts = {}) {
            this.title = opts.title
            this.message = opts.message
            this.okButton = opts.okButton
            if (opts.cancelButton) {
                this.cancelButton = opts.cancelButton
            }
            // Once we set our config, we tell the popup modal to open
            this.$refs.popup.open()
            // Return promise so the caller can get results
            return new Promise((resolve, reject) => {
                this.resolvePromise = resolve
                this.rejectPromise = reject
            })
        },

        _confirm() {
            this.$refs.popup.close()
            this.resolvePromise(true)
        },

        _cancel() {
            this.$refs.popup.close()
            this.resolvePromise(false)
            // Or you can throw an error
            // this.rejectPromise(new Error('User cancelled the dialogue'))
        },
    },
}
</script>