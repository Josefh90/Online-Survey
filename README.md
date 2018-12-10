# VueJS + SurveyJS/SurveyJS_Editor QuickStart Source
[![Build Status][travis-badge]][travis-badge-url]

## How to run this sample application
 - git clone https://github.com/surveyjs/surveyjs_vue_quickstart.git
 - cd surveyjs_vue_quickstart
 - npm i
 - npm run dev
 - open http://localhost:8080/ in your web browser


For detailed explanation on how VueJS things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## Add survey component on your page
```JavaScript
<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- If you want to show survey, uncomment the line below -->
    <!-- <survey :survey="survey"></survey> -->
    <!-- If you want to show survey editor, uncomment the line below -->
    <!-- <survey-editor></survey-editor> -->
    <survey-editor></survey-editor>
  </div>
</template>

<script>
//In your VueJS App.vue or yourComponent.vue file add these lines to import
import SurveyEditor from './components/SurveyEditor'
import * as SurveyVue from 'survey-vue'
import 'bootstrap/dist/css/bootstrap.css';

var Survey = SurveyVue.Survey
Survey.cssType = "bootstrap";

//If you want to add custom widgets package
//Add these imports
import * as widgets from "surveyjs-widgets";
import "inputmask/dist/inputmask/phone-codes/phone.js";
//And initialize widgets you are want ti use
widgets.icheck(SurveyVue);
widgets.select2(SurveyVue);
widgets.inputmask(SurveyVue);
widgets.jquerybarrating(SurveyVue);
widgets.jqueryuidatepicker(SurveyVue);
widgets.nouislider(SurveyVue);
widgets.select2tagbox(SurveyVue);
widgets.signaturepad(SurveyVue);
widgets.sortablejs(SurveyVue);
widgets.ckeditor(SurveyVue);
widgets.autocomplete(SurveyVue);
widgets.bootstrapslider(SurveyVue);

export default {
  name: 'app',
  components: {
    Survey,
    SurveyEditor
  },
  data () {
    //Define Survey JSON
    //Here is the simplest Survey with one text question
    var json = {
     elements: [
      { type: "text", name: "customerName", title: "What is your name?", isRequired: true}
     ]
    };
    
    //Create the model and pass it into VueSJ Survey component
    var model = new SurveyVue.Model(json)
    //You may set model properties
    // model.mode="display"

    return {
        survey: model
    }
  }
}
</script>
```
#   O n l i n e - S u r v e y  
 