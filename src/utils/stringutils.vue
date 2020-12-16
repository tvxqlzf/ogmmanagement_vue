<template>
  <div class="app-container">
    <upload
    :action="action"
    :limit="limitNum"
    :accept="accept"
    :auto-upload="autoUpload"
    />
  </div>
</template>

<script>
// import Upload from "@/components/Upload";

import Upload from './upload'

export default {
  name: 'UploadFiles',
  components: { Upload },
  data () {
    return {
      action: '/uploadFiles/pc/job/uploadFile',
      limitNum: 3,
      accept: '.xlsx,.vue,.png,PNG',
      autoUpload: false
    }
  },
  methods: {

  }
}
</script>