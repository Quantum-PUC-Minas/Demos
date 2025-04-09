# Qiskit
O nome "Qiskit" é um termo geral que se refere a uma coleção de softwares para desenvolvimento de algoritmos e circuitos quanticos, permitindo a execução do software simulando um hardware quantico localmente ou acessando serviços de nuvem da IBM pelo Qiskit Runtime e executando o software em Unidades de Processamento Quântico Reais (QPUs).

&nbsp;
## Tutorial de Instalação do Qiskit

### 🐍 Python
Consulte a seção "Linguagem de Programação" na página [Qiskit PyPI](https://pypi.org/project/qiskit/) para determinar quais versões do Python são suportadas pela versão mais recente do Qiskit. Instale o Python em https://www.python.org/dow

Verifique a versão do Python no com o comando:
```
python --version
```


### ⚙️ SDK
Instale o Qiskit SDK para ter acesso a todas as ferramentas de desenvolvimento:
```
pip install qiskit
```


### 🔃 Runtime
Instale o Qiskit Runtime para acessar os recursos de computação em nuvem da IBM:
```
pip install qiskit-ibm-runtime
```

&nbsp;
## Computação Quântica em Nuvem
Você pode acessar unidades de processamento quântico (QPUs) da IBM® usando o canal da IBM Quantum Platform ou da IBM Cloud®. Neste tutorial iremos utilizar o IBM Quantum Platform, que possui os seguintes planos

- Plano Open (acesso gratuito) - Execute seus circuitos quânticos nas melhores QPUs do mundo gratuitamente (até 10 minutos de tempo quântico por mês).

- Plano Premium (assinatura corporativa) - Execute circuitos quânticos nas melhores QPUs do mundo usando uma assinatura de tempo quântico corporativa.

> [!WARNING]
> Antes de configurar a IBM Quantum Platform, certifique-se de ter o Qiskit SDK e o Qiskit Runtime instalados.

&nbsp;
## Conectando com a Nuvem da IBM

Se você ainda não possui uma conta de usuário, crie uma na [página de login do IBM Quantum](https://quantum.ibm.com/). Sua conta de usuário está associada a uma ou mais instâncias (no formato hub/grupo/projeto) que dão acesso aos serviços do IBM Quantum.

- Além disso, um token exclusivo é atribuído a cada conta, permitindo acesso ao IBM Quantum a partir do Qiskit.

  ![fgdfgd](https://github.com/user-attachments/assets/f2a6b212-0e86-4cca-9364-d1d02febbf8a)

Se você estiver trabalhando em um ambiente Python confiável (como em um laptop ou estação de trabalho pessoal), use o método **save_account()** para salvar suas credenciais localmente.

```Q#
from qiskit_ibm_runtime import QiskitRuntimeService

token = "<your-token>"

QiskitRuntimeService.save_account(
  token=token,
  channel="ibm_quantum" # `channel` distinguishes between different account types
)
```







<!-- - ### Ferramentas de construção de circuitos
  ``` (qiskit.circuit) ```
  Para inicializar e manipular registradores, circuitos, instruções, portas, parâmetros e objetos de fluxo de controle.
  
- ### Biblioteca de circuitos
  ``` (qiskit.circuit.library)```
  Coleção com uma vasta gama de circuitos, instruções e portas.

- ### Biblioteca de informações quânticas
  ```(qiskit.quantum_info)``` Um kit de ferramentas para trabalhar com estados, operadores e canais quânticos, usando cálculos exatos (sem ruído de amostragem). Use este módulo para especificar observáveis ​​de entrada e analisar a fidelidade das saídas de consultas de primitivas.

- ### Transpiler
  ```(qiskit.transpiler)``` Para transformar e adaptar circuitos quânticos para se adequarem à determinados dispositivos e otimizar para execução em unidades de processamento quântico (QPUs) reais.

- ## Primitivas
  ```(qiskit.primitives)``` - O módulo que contém as definições básicas e implementações de referência das primitivas Sampler e Estimator, a partir das quais diferentes fornecedores de hardware quântico podem derivar suas próprias implementações.



