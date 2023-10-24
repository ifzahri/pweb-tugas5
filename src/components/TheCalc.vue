<template>
  <div class="container-fluid">
    <h1 class="display-5 fw-bold">Tugas 5</h1>
    <p class="col-md-8 fs-4">Membuat aplikasi kalkulator (Vue JS)</p>
    <div class="container-fluid py-5" id="calculator">
      <div class="row g-3">
        <div class="col-6 mb-3">
          <input
            type="number"
            class="form-control"
            id="num1"
            placeholder="Masukkan nomor ke-1"
            v-model="num1"
          />
        </div>
        <div class="col-6 mb-3">
          <input
            type="number"
            class="form-control"
            id="num2"
            placeholder="Masukkan nomor ke-2"
            v-model="num2"
          />
        </div>
      </div>
      <div class="mb-3">
        <button class="operator-btn btn btn-dark" id="setOperatoradd" @click="setOperator('+')">
          +
        </button>
        <button class="operator-btn btn btn-dark" id="setOperatorsub" @click="setOperator('-')">
          -
        </button>
        <button class="operator-btn btn btn-dark" id="setOperatormul" @click="setOperator('*')">
          *
        </button>
        <button class="operator-btn btn btn-dark" id="setOperatordiv" @click="setOperator('/')">
          /
        </button>
        <button class="btn btn-primary" id="calculate" @click="calculate">Hitung</button>
      </div>
      <p>
        Hasil: <span id="hasil">{{ hasil }}</span>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: 0,
      num2: 0,
      hasil: '-',
      select: '+'
    }
  },
  methods: {
    setOperator(operator) {
      this.select = operator
      document.querySelector('.operator-btn.selected').classList.remove('selected')
      document.querySelector(`button[data-operator="${operator}"]`).classList.add('selected')
    },
    calculate() {
      const num1 = parseFloat(this.num1)
      const num2 = parseFloat(this.num2)
      let result

      switch (this.select) {
        case '+':
          result = num1 + num2
          break
        case '-':
          result = num1 - num2
          break
        case '*':
          result = num1 * num2
          break
        case '/':
          if (num2 !== 0) {
            result = num1 / num2
          } else {
            result = 'Tidak bisa dibagi dengan 0'
          }
          break
        default:
          result = 'Invalid'
      }

      this.hasil = result
    }
  }
}
</script>
