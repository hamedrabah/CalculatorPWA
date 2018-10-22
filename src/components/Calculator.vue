<template>
    <v-app id='calculator'>
        <v-content>
            <v-container>
                <v-alert v-model="formulaAlert" dismissible type="error">Invalid Formula</v-alert>
                <v-layout  align-start justify-space-around fill-height>
                <v-text-field clearable v-model="formula">
                </v-text-field>    
                <v-btn @click="evaluate()"> = </v-btn>
                </v-layout> 

                 <v-layout row wrap> 
                <v-btn @click="append(7)">7</v-btn>
                <v-btn @click="append(8)">8</v-btn>
                <v-btn @click="append(9)">9</v-btn>
                <v-btn @click="append('+')">+</v-btn>
                
                 </v-layout>
                <v-layout row wrap> 
                <v-btn @click="append(4)">4</v-btn>
                <v-btn @click="append(5)">5</v-btn>
                <v-btn @click="append(6)">6</v-btn>
                <v-btn @click="append('-')">-</v-btn>
                
                </v-layout>
                <v-layout row wrap> 
                <v-btn @click="append(1)">1</v-btn>
                <v-btn @click="append(2)">2</v-btn>
                <v-btn @click="append(3)">3</v-btn>
                <v-btn @click="append('*')">*</v-btn>
                
                </v-layout>
                <v-layout row wrap> 
                <v-btn @click="append(null)">CLEAR</v-btn>
                <v-btn @click="append('0')">0</v-btn>
                <v-btn @click="append('.')">.</v-btn>
                <v-btn @click="append('/')">/</v-btn>
                
                </v-layout>
       
            </v-container>
        </v-content>
    </v-app>
</template>

<script>
export default {
  data() {
    return {
      formula: "",
      formulaAlert: false
    };
  },
  methods: {
    evaluate(num) {
      try {
        /* WARNING! Never use eval in production code. */

        let result = eval(this.formula);
        this.formulaAlert = false;
        this.formula = result;
      } catch (exception) {
        this.formulaAlert = true;
      }
    },
        append(num) {
        if (num==null){ 
        this.formula="";
        } else { 
          this.formula+=num;
        }
    }
  }
};
</script>

<style scoped>
</style>
