<template id="flag-dropdown" >
    <div class="lang-dropdown">
      <div class="flag-box">
        <span v-bind:class="'flag flag-'+selected"></span> 
      </div>

      <div class="lang-dropdown-content">
        <ul>
          <li v-for="c in countries" v-on:click="onFlagChange(c.id, c.phonecode, c.iso)">
            <i v-bind:class="'flag flag-'+c.iso"></i>
            <span>{{ c.iso }} (+{{ c.phonecode }})</span>
          </li>
        </ul>
      </div>
    </div>
</template>

<script>
  export default {
    props: {
      selected: {
        type: String,
        required: true
      },
      countries: {
        type: Array, 
        required: false,
      },
    },
    
    template: '#flag-dropdown',

    methods: {
      onFlagChange: function (id, phonecode, iso) {
        var data = { 'id' : id, 'phonecode' : phonecode, 'iso' : iso };
        this.$emit('change', data);
      },
    }
  }
</script>
