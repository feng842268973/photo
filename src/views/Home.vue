<template>
  <div class="home">
    <img class="img" src="../../images/test.jpg" alt="">
   <button @click="getimage">getimage</button>
    
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  data(){
    return {
      
    }
  },
  computed:{
    img(){
      return this.getBase64Image(document.querySelector('.img'))
    }
  },
  methods:{
    getBase64Image(img) {  
      var canvas = document.createElement("canvas");  
      canvas.width = img.width/2;  
      canvas.height = img.height/2;  
      var ctx = canvas.getContext("2d");  
      ctx.drawImage(img, 0, 0, img.width, img.height);  
      var ext = img.src.substring(img.src.lastIndexOf(".")+1).toLowerCase();  
      var dataURL = canvas.toDataURL("image/"+ext);  
      return dataURL.slice(22);  
  } ,
    getimage(){
    //access_token  

      let tk=  '24.ae176569874e3d14813a532449f936d5.2592000.1611307231.282335-23131836'
      let rectangle=[{'width': 200, 'top': 0, 'height': 345, 'left': 0}]
      this.$axios.post(
        '/rest/2.0/image-process/v1/inpainting?access_token='+tk,
        {
          rectangle:rectangle,
          // image:this.getBase64Image(this.img)
          image:this.img
        }
      ).then(res=>{
        console.log(res)
      })
    }
  }
}
</script>
