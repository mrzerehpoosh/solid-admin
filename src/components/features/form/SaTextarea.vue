<template>
  <!--
      Form's label and textarea component with standard HTML5 attributes

      Usage:
        <sa-textarea label='label' name='name' id='id' 
                     placeholder='placeholder' 
                     v-model='data'
                     color='success/danger/info/warning'
                     flow='horizontal/vertical'
                    :required='true/false'
                    text-align='left/right'
                    :asterisk='true/false'
        >
        </sa-textarea>

        * 'label' property is the only required one
        * default flow     = 'vertical'
        * default required = 'false'
        * default asterisk = 'false'
  -->
  <div class="field">
    <!--
      Template when textarea is vertical (default)
    -->
    <div class="field" :class="{'has-text-right': isRtl}" v-if="flow === 'vertical'">
      <label class="label" :class="directionClass" :for="id">
        <span>{{label}}</span>
        <span class="has-text-danger" v-if="asterisk">&nbsp;&#42;</span>
      </label>
      <p class="control">
        <textarea class="textarea" :name="name" :id="id" 
                  :placeholder="placeholder" :required="required"
                  :class="[textAlignClass, directionClass, ` is-${color}`]" :disabled="disabled" 
                  :value="value" @input="updateValue($event.target.value)" ref="input"
        >
        </textarea>
      </p>
    </div>

    <!--
      Template when textarea is horizontal
    -->
    <div class="field is-horizontal" 
        :class="{'has-text-right sa-row-reverse': isRtl}" 
        v-else-if="flow === 'horizontal'"
    >
      <div class="field-label is-normal" :class="{'sa-form-horizontal-label': isRtl}">
        <label class="label" :class="directionClass" :for="id">
          <span>{{label}}</span>
          <span class="has-text-danger" v-if="asterisk">&nbsp;&#42;</span>
        </label>
      </div>
      <div class="field-body">
        <div class="field">
          <div class="control">
            <textarea class="textarea" :name="name" :id="id" 
                      :placeholder="placeholder" :required="required" 
                      :class="[textAlignClass, directionClass, ` is-${color}`]" :disabled="disabled"
                      :value="value" @input="updateValue($event.target.value)" ref="input"
            >
            </textarea>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import TextInputMixin from './TextInputMixin.js';

export default {
  name: 'Textarea',
  mixins: [TextInputMixin]
}
</script>

