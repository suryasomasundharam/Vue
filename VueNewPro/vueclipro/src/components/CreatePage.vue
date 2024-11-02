<template>
    <div class="container mb-3">
        <form @submit.prevent="submitForm">
            <div class="mb-3">
                <label for="pageTitle" class="form-label">Page Title</label>
                <input type="text" id="pageTitle" class="form-control" v-model="pageTitle" />
            </div>
            <div class="mb-3">
                <label for="content" class="form-label">Content</label>
                <textarea id="content" class="form-control" v-model="content"></textarea>
            </div>
            <div class="mb-3">
                <label for="linkUrl" class="form-label">URL</label>
                <input type="text" id="linkUrl" class="form-control" v-model="linkUrl" />
            </div>
            <div class="mb-3">
                <label for="linkText" class="form-label">Link Text</label>
                <input type="text" id="linkText" class="form-control" v-model="linkText" />
            </div>
            <div class="mb-3 form-check">
                <input type="checkbox" class="form-check-input" id="satisfied" />
                <label for="satisfied" class="form-check-label">Satisfied</label>
            </div>
            <div class="mb-3">
                <button type="submit" class="btn btn-primary"
                :disabled="isFormValid"
                @click.prevent="submitForm"
                >Create Page</button>
            </div>
        </form>
    </div>
</template>

<script>
export default {
    props: ['pageCreated'],
    computed :{
      isFormValid(){
        return !this.pageTitle || !this.content || !this.linkText || !this.linkUrl
      }
    },
    data() {
        return {
            pageTitle: '',
            content: '',
            linkText: '',
            linkUrl: ''
        };
    },
    methods: {
        submitForm() {
            if (!this.pageTitle || !this.content || !this.linkText || !this.linkUrl) {
                alert('Please fill out the form.');
                return;
            }
            this.pageCreated({
                pageTitle: this.pageTitle,
                content: this.content,
                link: {
                    text: this.linkText,
                    url: this.linkUrl
                }
            });
        }
    }
};
</script>
