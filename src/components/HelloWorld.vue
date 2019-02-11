<template>
  <div class="hello">
    <p class="setting">
      <label for="debug-network">
        {{ network }}
        <input id="is-debug-network" type="checkbox" v-model="debug">Debug
      </label>
    </p>
    <hr>
    <div class="main" v-if="scatter">
      <p v-if="!currentAccount">
        <button @click="login">Login</button>
      </p>
      <div class="content" v-else>
        {{currentAccount}}
        <button @click="logout">Logout</button>

        <hr>
        <p>
          <button @click="send">Demo 1: Transfer EOS to whatsupto123</button>
        </p>
        <p>
          <button @click="getMyBalance">Demo 4: Get My EOS Balance</button>
        </p>
        <p>
          <input type="text" placeholder="data to be sign" v-model="dataTobeSign">
          <label for="is-hash">
            <input id="is-hash" type="checkbox" v-model="isHash">
            isHash
          </label>
          <input type="text" placeholder="what for" v-model="whatfor">
        </p>
        <p>
          <button @click="getArbitrarySignature">Demo 5: getArbitrarySignature</button>
        </p>
        <p><button @click="suggestNetwork">Demo 6: suggestNetwork</button></p>
        <p><button @click="getPublicKey">Demo 7: getPublicKey</button></p>
        
        <p><button @click="linkAccount">Demo 8: linkAccount</button></p>
        <p><button @click="requestTransfer">Demo 9: requestTransfer</button></p>
        
      </div>
    </div>
    <p class="copyright">
      <hr />
      @Scatter Desktop v{{version ? version : "0.0.0"}}
    </p>
  </div>

</template>

<script>
import Eos from "eosjs";
import ScatterJS from "scatterjs-core";
import ScatterEOS from "scatterjs-plugin-eosjs";

ScatterJS.plugins(new ScatterEOS());

const testNetwork = {
  blockchain: "eos",
  host: "145.239.133.201",
  port: 8888,
  protocol: "http",
  chainId: "e70aaab8997e1dfce58fbfac80cbbb8fecec7b99cf982a9444273cbc64c41473"
};

const prodNetwork = {
  blockchain: "eos",
  host: "mainnet.eoscanada.com",
  port: 443,
  protocol: "https",
  chainId: "aca376f206b8fc25a6ed44dbdc66547c36c6c33e3a119ffbeaef943642f0e906"
};

let network = prodNetwork;


// Put eosClient in data will case a weird problem in scatter-desktop.
let eosClient = null;

let requiredFields = { accounts: [network] };

export default {
  name: "HelloWorld",
  data() {
    return {
      currentAccount: null,
      currentPermission: null,
      scatter: null,
      readOnlyEos: null,
      pubKey: null,
      dataTobeSign: "",
      whatfor: "tp-demo",
      isHash: false,
      version: "",
      debug: false,
      network: network.host,
    };
  },
  created() {
    let chainId = network.chainId;
    let httpEndpoint =
      network.protocol + "://" + network.host + ":" + network.port;

    this.readOnlyEos = Eos({
      chainId,
      httpEndpoint
    });

    ScatterJS.scatter.connect("scatter-demo").then(connected => {
      // User does not have Scatter Desktop, Mobile or Classic installed.
      if (!connected) return false;

      this.scatter = ScatterJS.scatter;

      window.scatter = null;
      window.ScatterJS = null;
    });
  },
  methods: {
    queryTPT() {
      // this.readOnlyEos
      //   .getTableRows(true, "eosiotptoken", "eosiotptoken", "global")
      //   .then(data => {
      //     alert("TPT Total Staked: " + data.rows[0].total_delegate_quantity);
      //   });
    },
    login() {

      network = this.debug ? testNetwork : prodNetwork;
      requiredFields = { accounts: [network] };
      this.network = network.host;

      this.scatter
        .getIdentity(requiredFields)
        .then(() => {
          
          const account = this.scatter.identity.accounts.find(
            x => x.blockchain === "eos"
          );

          let scatter = this.scatter;

          this.pubKey = this.scatter.identity.publicKey;

          this.currentAccount = account.name;
          this.currentPermission = account.authority;
          eosClient = this.scatter.eos(network, Eos);

          // get scatter desktop version
          this.getVersion();

        })
        .catch(err => {
          alert(JSON.stringify(err));
        });
    },
    logout() {
      this.scatter.forgetIdentity();
      this.currentAccount = null;
      this.currentPermission = null;
    },
    send() {
      alert("not implement!!!")
      // eosClient
      //   .transfer(
      //     this.currentAccount,
      //     "whatsupto123",
      //     "0.0001 EOS",
      //     "from scatter-demo"
      //   )
      //   .then(data => {
      //     alert("succeed");
      //     console.log(data);
      //   })
      //   .catch(err => {
      //     alert(JSON.stringify(err));
      //   });
    },
    vote() {
      alert("not implement!!!")
      // eosClient
      //   .transaction({
      //     actions: [
      //       {
      //         account: "eosio",
      //         name: "voteproducer",
      //         authorization: [
      //           {
      //             actor: this.currentAccount,
      //             permission: this.currentPermission
      //           }
      //         ],
      //         data: {
      //           voter: this.currentAccount,
      //           proxy: "",
      //           producers: ["itokenpocket"]
      //         }
      //       }
      //     ]
      //   })
      //   .then(data => {
      //     alert("succeed");
      //     console.log(data);
      //   })
      //   .catch(err => {
      //     alert(JSON.stringify(err));
        // });
    },
    airgrabContract() {
      alert("not implement!!!")
      // eosClient.contract("poormantoken").then(contract => {
      //   contract
      //     .signup(this.currentAccount, "0.0000 POOR")
      //     .then(data => {
      //       alert("succeed");
      //       console.log(data);
      //     })
      //     .catch(err => {
      //       alert(JSON.stringify(err));
      //     });
      // });
    },
    getMyBalance() {

      eosClient
        .getCurrencyBalance("eosio.token", this.currentAccount, "EOS")
        .then(data => {
          alert(this.currentAccount + ": " + data[0]);
        });
    },
    getArbitrarySignature() {
      this.scatter
        .getArbitrarySignature(
          this.pubKey,
          this.dataTobeSign || "tokenpocket",
          this.whatfor,
          this.isHash
        )
        .then(data => {
          alert(data);
        })
        .catch(err => {
          alert("error:" + err);
        });
    },
    getVersion() {
      this.scatter.getVersion().then(v => {
        this.version = v;
      }).catch(alert);
    },
    suggestNetwork() {
      this.scatter.suggestNetwork(network).then(added => {
        alert(added);
      }).catch(err => console.log("error: ", JSON.stringify(err)));
    },
    getPublicKey() {
      const blockchain = "eos";
      this.scatter.getPublicKey(blockchain).then(publicKey => {
        alert(publicKey);
      }).catch(err => console.log("error: ", JSON.stringify(err)));
    },
    linkAccount() {
      const account = {
        name: this.currentAccount,
        authority: this.currentPermission,
        publicKey: "EOS7cZMPEEo3EMHWkRJ7zHv3dQNvZDUHi71tHitNPqht8zwppdFXZ" || this.pubKey
      };

      this.scatter.linkAccount(account, network).then(linked => {
        alert(linked);
      }).catch(err => console.log("error: ", JSON.stringify(err)));
    },
    requestTransfer() {
      const tokenDetails = {contract:'eosio.token', symbol:'EOS', memo:'', decimals:4};
      const to = "whatsupto123";
      const amount = "0.0001";
      this.scatter.requestTransfer(network, to, amount, tokenDetails).then(result => {
          console.log('result', result);
      }).catch(err => console.log("error: ", JSON.stringify(err)));
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  padding: 6px 12px;
  background-color: #da9c11;
}

hr {
  width: 90%;
  border: none;
  border-top: 1px solid #f1f1f1;
}

.hello {
  text-align: center;
}

.setting {
  text-align: right;
  margin-right: 5%;
}

.copyright {
  text-align: center;
}

.main {
  text-align: center;
}
.content {
  text-align: left;
}
</style>
