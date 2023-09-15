<template>
  <div>
    <h1>Meu Banco</h1>
    <p :style="{ color: saldo >= 0 ? 'green' : 'red' }">Saldo: R$ {{ saldo.toFixed(2) }}</p>
    <button @click="depositar">Depositar</button>
    <button @click="sacar">Sacar</button>
  </div>
</template>  
<script>
export default {
  name: `Banco`,
  data() {
    return {
      saldo: 100.0,
    };
  },
  methods: {
    depositar() {
      const valor = parseFloat(prompt('Digite o valor do depósito:'));
      if (!isNaN(valor) && valor > 0) {
        this.saldo += valor;
      }
    },
    sacar() {
      const valor = parseFloat(prompt('Digite o valor do saque:'));
      if (!isNaN(valor) && valor > 0) {
        if (this.saldo >= valor) {
          this.saldo -= valor;
        } else {
          // Se o saldo não for suficiente, apenas subtrai o valor do saldo
          // Isso fará com que o saldo fique negativo
          this.saldo -= valor;
        }
      }
    },
  },
};
</script>

  