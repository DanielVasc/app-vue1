<script>
import { ref } from 'vue';

export default {
  setup() {
    let nome = ref("");
    let email = ref("");
    let nascimento = ref(null);
    let bio = ref("")
    const senha = ref('senha');
    const Csenha = ref('Csenha');
    const SEst = ref("");
    const SHob = ref([]);
    const SLing = ref([]);

    const estados = ref([
      { id: "Acre", name: "AC" },
      { id: "Alagoas", name: "AL" },
      { id: "Amapá", name: "AP" },
      { id: "Amazonas", name: "AM" },
      { id: "Bahia", name: "BA" },
      { id: "Ceará", name: "CE" },
      { id: "Distrito Federal", name: "DF" },
      { id: "Espírito Santo", name: "ES" },
      { id: "Goiás", name: "GO" },
      { id: "Maranhão", name: "MA" },
      { id: "Mato Grosso", name: "MT" },
      { id: "Mato Grosso do Sul", name: "MS" },
      { id: "Minas Gerais", name: "MG" },
      { id: "Pará", name: "PA" },
      { id: "Paraíba", name: "PB" },
      { id: "Paraná", name: "PR" },
      { id: "Pernambuco", name: "PE" },
      { id: "Piauí", name: "PI" },
      { id: "Rio de Janeiro", name: "RJ" },
      { id: "Rio Grande do Norte", name: "RN" },
      { id: "Rio Grande do Sul", name: "RS" },
      { id: "Rondônia", name: "RO" },
      { id: "Roraima", name: "RR" },
      { id: "Santa Catarina ",name: "SC" },
      { id: "São Paulo", name: "SP" },
      { id: "Sergipe", name: "SE" },
      { id: "Tocantins", name: "TO" },
    ]);

    const hobs = ref([
      { id: "Futebol", name: "Futebol" },
      { id: "Basquete", name: "Basquete" },
      { id: "Volei", name: "Volei" },
      { id: "Tênis", name: "Tênis" },
      { id: "Pesca", name: "Pesca" },
      { id: "Pintura", name: "Pintura" },
      { id: "Livros", name: "Livros" },
      { id: "Robotica", name: "Robotica" },
      { id: "Programação", name: "Programação" },
      { id: "Natação", name: "Natação" },
    ]);

    const linguagens = ref([
      { id: "Python", name: "Python" },
      { id: "JavaScript", name: "JavaScript" },
      { id: "Java", name: "Java" },
      { id: "C++", name: "C++" },
      { id: "Ruby", name: "Ruby" },
    ]);

    const Vsenha = () => {
      if (senha.value === Csenha.value) {
        return true;
      } else {
        alert("As senhas não são iguais");
        return false;
      }
    };

    const enviar = () => {
      if (Vsenha()) {
        const info = {
          nome: nome.value,
          email: email.value,
          nascimento: nascimento.value,
          estado: SEst.value,
          hob: SHob.value,
          linguagens: SLing.value,
          biografia: bio.value,
        };
        alert(`Informações: \n${JSON.stringify(info, null, 2)}`);
      }
    };

    return {
      nome,
      email,
      nascimento,
      bio,
      senha,
      Csenha,
      SEst,
      SHob,
      SLing,
      estados,
      hobs,
      linguagens,
      Vsenha,
      enviar,
    };
  },
};
</script>

<template>
  <form @submit.prevent="enviar">
    <div class="info">
      <div>
        <input type="text" v-model="nome" minlength="3" maxlength="20" placeholder="digite seu nome" />
        <input type="email" v-model="email" placeholder="digite seu email" />
        <input type="date" v-model="nascimento" placeholder="data de nascimento"/>
      </div>
      <div>
        <input required type="password" v-model="senha" placeholder="Senha" />
        <input required type="password" v-model="Csenha" placeholder="Confirmar Senha" />
      </div>
    </div>

    <div class="estado">
      <select v-model="SEst">
        <option disabled value="">Selecione o estado</option>
        <option v-for="(estado, index) in estados" :key="index" :value="estado.id">
          {{ estado.name }}
        </option>
      </select>
      <span> {{ SEst }} </span>
    </div>

    <div class="hobs">
      <label>Qual seu hob</label>
      <div v-for="(hob, index) in hobs" :key="index">
        <input type="checkbox" v-model="SHob" :value="hob.id" :id="hob.id" />
        <label :for="hob.id">{{ hob.name }}</label>
      </div>
      <span> {{ SHob }} </span>
    </div>

    <div class="ling">
      <label>Quais as linguagens que voce conhece</label>
      <div v-for="(ling, index) in linguagens" :key="index">
        <input type="checkbox" v-model="SLing" :value="ling.id" :id="ling.id" />
        <label :for="ling.id">{{ ling.name }}</label>
      </div>
      <span> {{ SLing }} </span>
    </div>

    <p>Escreva sua biografia</p>
    <textarea v-model="bio" />
    <p style="white-space: pre-line;">
    </p>

    <div class="col-12">
      <button class="btn btn-primary" type="submit">Enviar</button>
    </div>
  </form>
</template>

<style>
.info {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  border: 1px solid #575353;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #beb5b5;
  color: #000000;
}

.estado {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  border: 1px solid #3f3c3c;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #beb5b5;
  color: #000000;
}

.hobs {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  border: 1px solid #555151;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #beb5b5;
  color: #000000;
}

.ling {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
  border: 1px solid #3d3b3b;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #beb5b5;
  color: #000000;
}

button[type="submit"] {
  background-color: #4d504d;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button[type="submit"]:hover {
  background-color: #676b67;
}
</style>