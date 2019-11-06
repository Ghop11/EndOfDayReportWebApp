<template>
  <div>
    <br>
    <center>
      <v-flex>
          <v-card max-width="600px">
            <v-card-title><center>END OF DAY REPORT - {{this.schoolSite}}</center></v-card-title>
            <v-card-text>
              <span>School site: {{this.schoolSite}}</span><br>
              <span>Visit Date: {{this.date}}</span><br>
              <span>Recap Summary: {{this.recap}}</span><br>
            </v-card-text>
            <v-spacer></v-spacer>
            <v-btn color="primary" @click="createPDF">Create PDF</v-btn>
            <v-card-text></v-card-text>
          </v-card>
      </v-flex>
    </center>
  </div>

</template>

<script>
    export default {
        name: "PdfHtml.vue",
        props: ['schoolSite', 'date', 'recap'],
        data() {
            return {

            }
        },
        methods: {
           createPDF: function () {
               this.$loadScript('https://pagecdn.io/lib/html2canvas/0.4.1/html2canvas.min.js')
                   .then(( ) => {
                       this.$loadScript('https://cdnjs.cloudflare.com/ajax/libs/jspdf/1.5.3/jspdf.debug.js')
                           .then(( ) => {
                               let pdf = jsPDF();
                               let img = "data:image/png;base64,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"

                               pdf.addImage(img, 'png', 65, 0);
                               pdf.setFontSize(22);
                               pdf.text(20,50,`End of Day Report - ${this.schoolSite}`, {maxWidth: 175});

                               pdf.setFontSize(14);
                               pdf.text(20,60,`Date: ${this.date}`);

                               let recap = this.recap.split('\n');

                               let y = 80;

                               if (recap.length == 0){
                                   pdf.text(20, 70, `Recap:`, {maxWidth: 175});
                                   pdf.text(20, y, `${this.recap}`, {maxWidth: 175});
                               } else {
                                   recap.forEach((p ) => {
                                       if(p !== ''){
                                           if (p.length > 70){
                                               pdf.text(20, y, `${p}`, {maxWidth: 175});
                                               let num = Math.floor(p.length / 90);
                                               let addNum = Math.floor((num) * 10);
                                               y += addNum;
                                           } else {
                                               pdf.text(20, y, `${p}`, {maxWidth: 175});
                                               y += 10;
                                           }
                                       }
                                   })
                               }
                               pdf.output('dataurlnewwindow', {filename: `${this.schoolSite}-${this.date}`});
                           })
                   })
           }
        },
    }
</script>

<style scoped>

</style>
