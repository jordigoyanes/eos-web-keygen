<template>
  <v-app>
    <v-container>
          <img src="/images/eos-icon.png" width="100px" height="100px"><h3 class="display-3">EOS Key Generator</h3>
          <span class="subheading">Here you can generate a valid EOS public and private key for your EOS ERC-20 tokens.</span>
          <span class="subheading">The keys are generated on the browser side using the <a href="https://github.com/EOSIO/eosjs-ecc">eosjs-ecc</a>  library. <br>You can run this web app locally in your computer as indicated in the <a href="https://github.com/jordigoyanes/eos-web-keygen">source code repository</a></span><br>
          <span class="subheading">Remember to save several copies of your keys, there is no way to restore your private key.</span><br>
          <span class="subheading">Built by <a href="https://twitter.com/jordi_goya">Jordi Goyanes</a>. Please consider donating some EOS to 0x3D936b62dd130308f46914e8580Bc0c337E05C27</span>
          <v-divider class="my-3"></v-divider>
          <div class="title mb-3">Public key: {{publicKey}}</div>
          <div class="title mb-3">Private key: {{privateKey}}</div>
          <v-tooltip bottom>
            <v-btn slot="activator" large color="primary" class="mx-0" @click.native="generateKeys">Generate keys</v-btn>
            <span>In Dan We Trust</span>
          </v-tooltip>
    </v-container>
  </v-app>
</template>

<script>
import ecc from 'eosjs-ecc';
  export default {
    data () {
      return {
        publicKey: '',
        privateKey: '',
      }
    },
    methods:{
      generateKeys: function(){
         ecc.randomKey().then(newPrivateKey => {
            this.privateKey = newPrivateKey;
            this.publicKey = ecc.privateToPublic(newPrivateKey);
        })
      }

    }
  }
</script>