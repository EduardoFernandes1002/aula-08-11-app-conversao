# Aula 08-11 - App Conversão de moeda

## Avaliação

* Implemente para que o usuário possa fazer conversão de outras moedas (mínimo + 3 moedas);
* Descreva abaixo o seu entendimento acerca desta atividade, explorando as funcionalidades das classes que contruímos e os principais pontos da aplicação;

## Entrega

* Clone este repositório e faça o que se pede;
* Realize um commit das suas alterações no seu repositório;
* Envie o link do repositório na avaliação gerada no classroom;

## Descritivo do Aluno:

### Sobre:
# App de Conversão de Moeda

## Descrição

Este é um aplicativo Android para converter moedas. O objetivo é permitir que o usuário converta valores entre diversas opções de moedas. O usuário seleciona a conversão que desejada, insere um valor e o aplicativo deve exibir o valor da conversão com base na taxa de câmbio atual.

# Aplicativo de Conversor de Moeda

## Funcionalidades

### Seleção de Moeda
O aplicativo oferece opções para conversão de moedas, incluindo:
- Real para Dólar
- Real para Euro
- Euro para Dólar
- Bitcoin para Real

### Conversão de Valor
O usuário digita o valor para ser convertido em um campo de texto e, ao clicar no botão para conversão, o resultado deve ser exibito exibido na tela com o valor convertido. 
Caso não seja selecionado deve aparecer um Erro.

### Taxas de Câmbio Atualizadas
O aplicativo recupera as taxas de câmbio por meio de uma API externa, garante que as conversões sejam feitas com valores atualizados ou o mais proximas das atuais.

## Pontos Chave e Classes


### 1. `MainActivity`
`MainActivity` é a parte principal da aplicação e com toda a lógica da interface e conversão de moeda.

#### **`MainActivity`** recursos:
- **Seleção de Conversão**: Ao escolher qual a conversão de moedas através de `RadioButtons`, e a conversão selecionada é guardada na variável chamada `opcaoSelecionada`.
  
- **Entrada de Valor**: Ao inserir o valor a ser convertido em um campo de texto. Clicando no botão “Converter”, o valor é enviado para a API de taxas de câmbio.

- **Solicitação de API**: A classe `AwesomeClient` é utilizada para fazer a solicitação à API externa, que retorna taxas de câmbio.

- **Cálculo e Exibição**: Com a taxa de câmbio recebida, o valor informado é convertido e o resultado é exibido em um `TextView`. Se ocorrer um erro, uma mensagem de erro será exibida usando `Toast`.

#### **`MainActivity`** fluxo:
1. Selecione a conversão de moeda.
2. Insira o valor a ser convertido.
3. Ao clicar em “Converter”, o aplicativo busca a taxa de câmbio na API.
4. O valor é convertido e o resultado é exibido.

### 2. `AwesomeClient`
A classe `AwesomeClient` é responsável por fazer requisições para a API externa `AwesomeAPI` e buscar as taxas de câmbio para as moedas selecionadas.  
- Utiliza a biblioteca `Retrofit` para simplificar as requisições HTTP.
- O cliente é configurado para usar o `ScalarsConverterFactory` para processar as respostas da API.
- A resposta da API é processada e passada para a `MainActivity` para exibição do resultado.

### 3. `ApiCallback`
A interface `ApiCallback` contém dois métodos:
- `onSuccess` para uma resposta bem-sucedida da API.
- `onError` para tratar erros durante a requisição.

### 4. `Gson`
A biblioteca `Gson` é usada para converter a resposta da API (em formato JSON) em objetos Java, permitindo que os dados sejam manipulados e utilizados no processo de conversão.

### 5. `ApiService`
`ApiService` define os métodos utilizados para fazer requisições à API externa de taxas de câmbio.  
- O método `getDados` especifica como o aplicativo busca as taxas de câmbio para as moedas selecionadas.
- A URL da API é configurada para aceitar um parâmetro dinâmico (o par de moedas), que será substituído na requisição.
- O método retorna um `Call<String>`, que representa a resposta da API em formato JSON.

## Como Usar

1. **Escolha a conversão desejada**:  
   O usuário seleciona a conversão de moeda utilizando os `RadioButtons` disponíveis na interface.

2. **Informe o valor**:  
   Após selecionar a conversão, o usuário insere o valor a ser convertido no campo de texto.

3. **Clique em "Converter"**:  
   Após o clique no botão, o aplicativo faz uma requisição à API, que realiza o cálculo e exibe o resultado da conversão.
