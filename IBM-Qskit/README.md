# Tutorial de Instalação do Qiskit
Qiskit é uma coleção de softwares para desenvolvimento de algoritmos e circuitos quanticos, permitindo a simulação de um hardware quantico localmente ou acessar serviços de nuvem da IBM e para computação em Processamento Quântico Reais (QPUs).
&nbsp;

&nbsp;

## 🐍 Instalar o Python
Consulte a seção "Linguagem de Programação" na página [Qiskit PyPI](https://pypi.org/project/qiskit/) para determinar quais versões do Python são suportadas pela versão mais recente do Qiskit. Instale o Python em https://www.python.org/dow

- Verifique a versão do Python no com o comando:
  
  ```
  python --version
  ```
> [!Note]
> A distribuição padrão do Python já possui um gerenciador de ambientes virtuais chamado [venv](https://python.land/virtual-environments/virtualenv). Para um melhor controle dos pacotes instalados é possível usar outras distribuições do Python como Anaconda ou Miniconda
&nbsp;

&nbsp;

## 🖥 Criando um Ambiente Virtual em Python no VSCode
Um ambiente virtual Python é uma cópia isolada do interpretador Python, bibliotecas e scripts. Ele é criado em uma subpasta de um projeto e é útil para evitar conflitos entre versões de pacotes.

- 1 Para criar um ambiente virtual, na pasta do seu projeto iremos abrir um terminal e digitar o seguinte comando
  ```
  python -m venv .myenv
  ```
- 2 Será criada uma pasta contendo o seu ambiente virtual, chamado myenv
  
  <img src="https://github.com/user-attachments/assets/f52361bf-4c28-4af9-99e5-aa14f8147c5d" alt="drawing" width="300"/>


- 3 Após isso irá aparecer a seguinte mensagem, clique em sim:
 
  <img src="https://github.com/user-attachments/assets/a1abd74c-b45b-4cc5-97db-204b1286dd40" alt="drawing" width="400"/>


- 4 Abrir um novo terminal para ver o seu ambiente funcionando
  
  <img src="https://github.com/user-attachments/assets/84e59251-ded3-49c8-a330-f0a5fac62565" alt="drawing" width="600"/>
  

  ⚠️ Se não funcionar é porque o ambiente foi criado porém ainda não está ativo, digite
  ```
  activate
   ```
- 4 No canto direito inferior podemos controlar qual ambiente estaremos utilizando
  
  <img src="https://github.com/user-attachments/assets/a2678453-f8cf-4d25-97a9-0704ffb3100f" alt="drawing" width="400"/>
  
- 5 Para Excluir um ambiente virtual é necessário desativa-lo antes, senão o vscode pode ficar travado nele
  ```
  deactivate
  ```
  e depos
  ```
  # If your virtual environment is in a directory called 'venv':
  rm -r venv
  ```
<br/>

## Instalação de Ferramentas Essenciais

### 🐍 Extensão Python
🛠 Instale a extensão do VSCODE 
https://marketplace.visualstudio.com/items/?itemName=ms-python.python

### ⚙️ SDK
Instale o Qiskit SDK para ter acesso a todas as ferramentas de desenvolvimento:
```
pip install qiskit
```


### 🧮 Visualização de Circuitos
Instale a ferramenta para pode visualizar os circuitos
```
pip install qiskit[visualization]
```

### 🔃 Qiskit Runtime
Instale o Qiskit Runtime para acessar os recursos de computação em nuvem da IBM:
```
pip install qiskit-ibm-runtime
```

### 🟡 Jupyter 
Shell interativo para seu ambiente python
```
pip install jupyter
```
🛠 Instale a extensão no VSCODE
https://marketplace.visualstudio.com/items/?itemName=ms-toolsai.jupyter
&nbsp;

&nbsp;
## Computação Quântica em Nuvem
Uma unidade de processamento quântico [QPU](https://www.ibm.com/think/topics/qpu) é um tipo de hardware de processamento de última geração que usa qubits (bits quânticos) para resolver problemas complexos usando a mecânica quântica. 

<img src="https://github.com/user-attachments/assets/ceb5015a-53f9-4899-b58f-58264e7de4ab" alt="drawing" width="500" height="250"/>
<img src="https://github.com/user-attachments/assets/b83f823b-1c2b-4da9-9d5f-ec12c6c50ce9" alt="drawing" width="500" height="250"/>
<br><br/>
Você pode realizar computações nas unidades de processamento quântico (QPUs) da IBM® usando o canal da IBM Quantum Platform ou da IBM Cloud®. Neste tutorial iremos utilizar IBM Quantum Platform, que possui o Plano Open Gratuito, permitindo executar seus circuitos quânticos nas melhores QPUs do mundo gratuitamente.
<br><br/>

> [!NOTE]
> O Plano Open permite até 10 minutos de processamento quantico por mês
&nbsp;

&nbsp;
## Conectar na Nuvem da IBM

### 1 Criando a conta
- Se você ainda não possui uma conta de usuário, crie uma na [página de login do IBM Quantum](https://quantum.ibm.com/). Sua conta de usuário está associada a uma ou mais instâncias (no formato hub/grupo/projeto)   que dão acesso aos serviços do IBM Quantum.
  
  ![image](https://github.com/user-attachments/assets/9e9e3a04-6d50-4e8a-a0d0-cce9684105da)

### 2 Credenciais
- Após a criação da conta, um token exclusivo é atribuído, permitindo acesso ao IBM Quantum a partir do Qiskit.
  
  ![fgdfgd](https://github.com/user-attachments/assets/f2a6b212-0e86-4cca-9364-d1d02febbf8a)

### 3 Testando o acesso

- Podemos acessar os recursos do IBM QuantumPlatform inserindo as credenciais no método QiskitRuntimeService()
  ```Q# 
  service = QiskitRuntimeService(channel="ibm_quantum", token="SEU-TOKEN-IBM") 
  ```

- Código para criar um circuito básico e executar em hardware quântico da IBM
  ```Q#
  from qiskit import QuantumCircuit
  from qiskit_ibm_runtime import QiskitRuntimeService, SamplerV2 as Sampler
   
  # Create empty circuit
  example_circuit = QuantumCircuit(2)
  example_circuit.measure_all()
   
  # You'll need to specify the credentials when initializing QiskitRuntimeService, if they were not previously saved.
  service = QiskitRuntimeService(channel="ibm_quantum", token="SEU-TOKEN-IBM") 
  backend = service.least_busy(operational=True, simulator=False)
   
  sampler = Sampler(backend)
  job = sampler.run([example_circuit])
  print(f"job id: {job.job_id()}")
  result = job.result()
  print(result)
  ```
- Resultado esperado ✅
  
  ![image](https://github.com/user-attachments/assets/e370fed8-d9e5-4073-ba32-b6c40c236b20)

- Se o ambiente não for confiável, é recomendado utilizar a chave no código normalmente e depois reseta-la no site da IBM
  
  ![thsdth](https://github.com/user-attachments/assets/f924c40a-05a1-4d80-a6f5-0db4824a3683)

&nbsp;

&nbsp;
## Salvando as as credenciais em um Ambiente Confiável
Se você estiver trabalhando em um ambiente Python confiável (como um laptop ou estação de trabalho pessoal), é possível salvar suas credenciais no seu ambiente utilizando o método save_account(). 

- Para usar save_account(), execute python no seu Shell (Anaconda ou Jupyter) e digite o seguinte:

   ```Q# 
  token = "<your-token>"
  ```
  
  ```Q# 
  from qiskit_ibm_runtime import QiskitRuntimeService
   
  QiskitRuntimeService.save_account(
    token=token,
    channel="ibm_quantum" # `channel` distinguishes between different account types
  )
  ```
- Utilizando o Shell do Jupyter no VSCODE
  
  <img src="https://github.com/user-attachments/assets/1dfd27ce-1e1f-4757-96fe-93296bab317a" width="400"/>

  <img src="https://github.com/user-attachments/assets/a10d0eef-5e78-49ad-95ae-0ce61c4e6c77" width="800"/>


- Dessa forma ao chamar o QiskitRuntime não será mais necessário salvar o token no código
  ```Q# 
  service = QiskitRuntimeService()
  ```
- Código para criar um circuito básico e executar em hardware quântico da IBM
  ```Q#
  from qiskit import QuantumCircuit
  from qiskit_ibm_runtime import QiskitRuntimeService, SamplerV2 as Sampler
   
  # Create empty circuit
  example_circuit = QuantumCircuit(2)
  example_circuit.measure_all()
   
  # You'll need to specify the credentials when initializing QiskitRuntimeService, if they were not previously saved.
  service = QiskitRuntimeService() 
  backend = service.least_busy(operational=True, simulator=False)
   
  sampler = Sampler(backend)
  job = sampler.run([example_circuit])
  print(f"job id: {job.job_id()}")
  result = job.result()
  print(result)
  ```
- Resultado esperado ✅
  ![image](https://github.com/user-attachments/assets/aa431816-84cd-4b44-a78b-ca4aec044f5f)



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



