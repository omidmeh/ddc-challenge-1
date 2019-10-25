<template>
  <div class="bx--grid bx--grid--full-width challenge-page">
    <div class="bx--row challenge-page__banner">
      <div class="bx--col-lg-16">
        <cv-breadcrumb noTrailingSlash>
          <cv-breadcrumb-item>
            <cv-link to="/challenge-page">Challenge 1</cv-link>
          </cv-breadcrumb-item>
        </cv-breadcrumb>
        <h1 class="challenge-page__heading">Your First App on IBM Cloud</h1>
      </div>
    </div>

    <div class="bx--row challenge-page__r2">
      <div class="bx--col bx--no-gutter">
        <cv-tabs @tab-selected="deactivate_t">
          <cv-tab label="And... We're Live!" :selected="t1_selected" :disabled="submission_tab_disabled">
            <div class="bx--grid bx--grid--no-gutter bx--grid--full-width">
              <div class="bx--row challenge-page__tab-content">
                <div class="bx--col-md-16 bx--col-lg-16">
                  <h1 class="challenge-page_didit">
                    <ThumbsUp32 aria-label="ThumbsUp Image" /> 
                     Yay... You did it! 
                    <div :style="{transform: 'scale(-1,1)', display: 'inline-block'}">
                      <ThumbsUp32 aria-label="ThumbsUp Image" />
                    </div>
                    </h1>
                    <br>
                  <p class="challenge-page_didit">
                    Congrats on your first app here!
                    <br>
                    Enter the following secret code back <u> in the challenge page</u> to mark it complete:
                    </p>
                    <br>
                    <div class="bx--col-sm-16 bx--col-md-4 bx--col-lg-4 bx--offset-sm-0 bx--offset-md-2 bx--offset-lg-6"> 
                      <cv-tile> 
                        <div class="secret_word">
                      potato
                    </div>
                     </cv-tile>
                    </div>

                    <br>
                    <br>
                    <br>
                    <br>
                    <br>
                    <br>

                  <!-- <img src="https://media.giphy.com/media/XreQmk7ETCak0/source.gif" alt=""> -->
                  <!-- <p class="challenge-page_didit">
                    <ThumbsUp32 aria-label="ThumbsUp Image" />
                  </p> -->
                  <p class="challenge-page_didit">
                    <cv-button :icon="Idea"  
                                @click="activate_t2">
                      Want more challenges?
                    </cv-button>
                  </p>
                </div>
              </div>
            </div>
          </cv-tab>
          <cv-tab label="More Challenges?"  :selected="t2_selected" :disabled="submission_tab_disabled">
            <div class="bx--grid bx--grid--no-gutter bx--grid--full-width">
              <div class="bx--row challenge-page__tab-content">
                <div class="bx--col-sm-16 bx--col-md-6 bx--col-lg-6 bx--offset-sm-0 bx--offset-md-1 bx--offset-lg-5 ">
                  <h1 class="">Make sure you've entered the secret code</h1>
                  <br>
                  <p class="">
                    Don't forget to enter the secret code from the previous page into your challenges page.
                    <br><br>
                    If you've done that, you're done. You can find even more challenges on the challenges page.
                    <br><br>
                    You're still reading this? Ok fine! If you've done all the challenges in the challenges page and are looking for something even 
                    more you <u> could </u> click  on the button below. But there's nothing there... at least, nothing useful!
                    
                    </p>
                    <br><br><br><br>
                    <div class="challenge-page_didit">
                      
                <cv-button :icon="Idea"  
                                @click="activate_t3">
                      I want to know what's behind this
                    </cv-button>
                    </div>
              </div>
                </div>
            </div>
          </cv-tab>
          <cv-tab label="Nothing here!" :selected="t3_selected">
            <div class="bx--grid bx--grid--no-gutter bx--grid--full-width">
              <div class="bx--row challenge-page__tab-content">
                <div class="bx--col-sm-16 bx--col-md-6 bx--col-lg-6 bx--offset-sm-0 bx--offset-md-1 bx--offset-lg-5">
                  <h1 class="">Now that you insist...</h1>
                  <br>
                  <p>
                    Like I said, you won't find anything good behind this. But if you must, go ahead!
                  </p>
                  <br><br><br><br><br>
                  <cv-button :icon="Idea"  
                                class="moving_button"
                                @click="activate_t3" 
                                id="running-button"
                                 @mouseover="move_button">
                      I'm a button, Click me
                    </cv-button>
                </div>
                
              </div>
            </div>
          </cv-tab>
        </cv-tabs>
      </div>
    </div>
  </div>
</template>

<script>
import AddFilled16 from '@carbon/icons-vue/es/add--filled/16';
import Notification20 from '@carbon/icons-vue/es/notification/20';
import UserAvatar20 from '@carbon/icons-vue/es/user--avatar/20';
import AppSwitcher20 from '@carbon/icons-vue/es/app-switcher/20';
import ThumbsUp32 from '@carbon/icons-vue/es/thumbs-up/32';
import Touch32 from '@carbon/icons-vue/es/touch--1/32';
import Play32 from "@carbon/icons-vue/es/play--filled--alt/32"
import moment from 'moment'
import validator from 'validator';

export default {
  name: 'ChallengePage',
  components: {
    Notification20,
    UserAvatar20,
    AppSwitcher20,
    ThumbsUp32,
    Touch32
  },
  data: function() {
    return {
      show: false,
      Idea: Play32,
      t1_selected: false,
      t2_selected: false,
      t3_selected: false,
      checkbox_value: false,
      input_email : "",
      toast_visible: false,
      toast_title: "",
      toast_subtitle: "",
      toast_caption: "",
      email_invalid: undefined,
      submission_active:false,
      submission_tab_disabled: false
    }
  },
  methods: {
      activate_t1: function() {
        this.t1_selected = true;
      },
      activate_t2: function() {
        this.t2_selected = true;
      },
      activate_t3: function() {
        this.t3_selected = true;
      },
      deactivate_t: function() {
        this.t1_selected = false
        this.t2_selected = false
        this.t3_selected = false
      },
      disable_submission_tabs: function() {
        this.submission_tab_disabled = true;
      },
      submit: function(e) {

        e.preventDefault();

        if(validator.isEmail(this.input_email)) {
          this.email_invalid=undefined;
        }else {
          this.email_invalid="Invalid Email";
          return;
        }

        this.submission_active = true;        
        var parent_obj = this;
        this.axios.post('https://digital-conference-responses-test.mybluemix.net/responses', {
          IBM_ID: this.input_email,
          APP_ID: "APPIDIDIDIDID",
          TIMESTAMP: moment().format(),
        })
        .then(function (response) {
          console.log("success");
          parent_obj.toast_visible = true;
          parent_obj.toast_title = "Success";
          parent_obj.toast_subtitle = "Your points are on their way";
          parent_obj.toast_caption = "This is the caption";
          // currentObj.output = response.data;
          parent_obj.submission_active = false;     
          parent_obj.disable_submission_tabs();   
          parent_obj.activate_t3()
        })
        .catch(function (error) {
          // console.log(error.response);
          parent_obj.toast_visible = true;
          parent_obj.toast_title = "Oops";
          parent_obj.toast_subtitle = "There was a problem";
          parent_obj.submission_active = false;     
          if (error.response.status === 409) {
            parent_obj.toast_caption = "I looks like you've already done this step. Your points should arrive soon!";
          } else {
            parent_obj.toast_caption = error.response.data.error.message;
          }
        });
      },
      doClose : function() {
        this.toast_visible = false;
      },
      move_button: function(event) {
        var caller = event.target;
        
        var randX = Math.floor(Math.random() * (window.innerWidth - 100));
        var randY = Math.floor(Math.random() * (window.innerHeight - 100));

        caller.style.left = randX+"px";
        caller.style.top = randY+"px";
      }
  },
  computed: {
    createdAtDisplay() {
      return moment().format();
    },
    notReadyForSubmit() {
      return !this.checkbox_value
      // return !(validator.isEmail(this.input_email))
    }
  }
};
</script>

<style lang="scss">
@import '../../styles/carbon-utils';
@import './carbon-overrides';
@import './mixins';

.challenge-page__banner {
  padding-top: $spacing-05;
  padding-bottom: $spacing-07 * 4;
  @include challenge-page-background;
}
.challenge-page__heading {
  @include carbon--type-style('expressive-heading-05');
}
.challenge-page__r2 {
  margin-top: rem(-40px);
}
.challenge-page__tab-content {
  padding-top: $layout-05;
  padding-bottom: $layout-05;
}

.challenge-page_didit {
  // @include carbon--type-style('display-04');
  // align-items: center;
  padding-bottom: $layout-02;
  text-align: center;
}

.challenge-page__subheading {
  @include carbon--type-style('expressive-heading-03');
  @include carbon--font-weight('semibold');
}

.challenge-page__p {
  @include carbon--type-style('expressive-heading-03');
  margin-top: $spacing-06;
  margin-bottom: $spacing-08;

  @include carbon--breakpoint-between((320px + 1), md) {
    max-width: 75%;
  }
}
.challenge-page__r3 {
  padding-top: $spacing-09;
  padding-bottom: $spacing-09;
  @include challenge-page-background;
}

.challenge-page__label {
  @include carbon--type-style('heading-01');
}

.secret_word {
  @include carbon--type-style('code-02');
  font-size:  rem(30px);
  text-align: center;
}
.blur {
  //  color: transparent;
  //  text-shadow: 0 0 15px rgba(0,0,0,0.9);
}

.moving_button {
    position: fixed;
    z-index: 2;   
}

</style>
