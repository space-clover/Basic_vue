<template>
  <ion-page>
    <ion-content fullscreen>
      <ion-card>
        <ion-card-content>
          <ion-input
            type="number"
            placeholder="Número 1"
            v-model="num1"
          ></ion-input>
          <ion-select
            placeholder="Operación"
            v-model="operation"
          >
            <ion-select-option value="+">Suma</ion-select-option>
            <ion-select-option value="-">Resta</ion-select-option>
            <ion-select-option value="*">Multiplicación</ion-select-option>
            <ion-select-option value="/">División</ion-select-option>
          </ion-select>
          <ion-input
            type="number"
            placeholder="Número 2"
            v-model="num2"
          ></ion-input>
          <ion-button expand="full" @click="performCalculation">Calcular</ion-button>
          <div>Resultado: {{ result }}</div>
        </ion-card-content>
      </ion-card>
    </ion-content>
  </ion-page>
</template>

<script>
export default {
  data() {
    return {
      num1: '',
      num2: '',
      operation: '',
      result: '',
    };
  },
  methods: {
    performCalculation() {
      if (this.num1 === '' || this.num2 === '' || this.operation === '') {
        this.result = 'Por favor, ingresa números y selecciona una operación.';
        return;
      }

      const n1 = parseFloat(this.num1);
      const n2 = parseFloat(this.num2);

      switch (this.operation) {
        case '+':
          this.result = n1 + n2;
          break;
        case '-':
          this.result = n1 - n2;
          break;
        case '*':
          this.result = n1 * n2;
          break;
        case '/':
          if (n2 === 0) {
            this.result = 'No se puede dividir por cero.';
          } else {
            this.result = n1 / n2;
          }
          break;
        default:
          this.result = 'Operación no válida.';
      }
    },
  },
};
</script>

