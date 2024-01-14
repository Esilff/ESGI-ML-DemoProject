<template>
    <img v-if="imageSource" :src="imageSource">
    <form @submit.prevent="checkFileType">
        Select a file to evaluate:
        <input type="file" name="fileToUpload" id="fileToUpload" ref="fileInput" @change="validateFile">
        <input type="submit" value="Upload File" name="submit">
    </form>
</template>
<script>
export default {
    name: 'ImageSelector',
    data() {
        return {
            imageSource: null
        }
    },
    methods: {
        validateFile() {
            const fileInput = this.$refs.fileInput;
            if (fileInput && fileInput.files.length > 0) {
                const file = fileInput.files[0];
                const fileName = file.name;
                const allowedExtensions = /\.(jpg|jpeg|png)$/i;
                if (!allowedExtensions.test(fileName)) {
                    alert('Please select a PNG or JPG image file.');
                    fileInput.value = '';
                }
            }
        },
        checkFileType(event) {
            const fileInput = this.$refs.fileInput;
            if (fileInput && fileInput.files.length > 0) {
                const file = fileInput.files[0];
                const fileName = file.name;
                const allowedExtensions = /\.(jpg|jpeg|png)$/i;
                if (!allowedExtensions.test(fileName)) {
                    alert('Only PNG or JPG image files are allowed.');
                    event.preventDefault();
                } else {
                    this.imageSource = URL.createObjectURL(file);
                }
            }
        }
    }
}
</script>