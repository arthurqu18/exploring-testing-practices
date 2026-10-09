# Explorando Práticas de Teste

Neste exercício, vamos explorar práticas de teste em sistemas reais utilizando a ferramenta [TestMiner](https://andrehora.github.io/testminer).

O TestMiner permite visualizar e analisar testes de software em repositórios do GitHub, fornecendo dados sobre como os projetos organizam seus testes, como eles evoluem entre versões e quais bibliotecas de teste são utilizadas.
Explore a ferramenta antes de começar para se familiarizar com seu funcionamento.

Mais detalhes no GitHub da ferramenta: https://github.com/andrehora/testminer.

---

## Passo 1: Selecionar um repositório

Escolha um repositório real que possua testes de software.
Abaixo estão alguns links para ajudá-lo a encontrar projetos interessantes:

- Python: https://github.com/topics/python?l=python
- JavaScript: https://github.com/topics/javascript?l=javascript
- TypeScript: https://github.com/topics/typescript?l=typescript
- Java: https://github.com/topics/java?l=java

- Tópicos: [ai](https://andrehora.github.io/testminer/#topic:ai), [llm](https://andrehora.github.io/testminer/#topic:llm), [api](https://andrehora.github.io/testminer/#topic:api), [nodejs](https://andrehora.github.io/testminer/#topic:nodejs), [android](https://andrehora.github.io/testminer/#topic:android)

- Por organização: [Google](https://andrehora.github.io/testminer/#google), [Microsoft](https://andrehora.github.io/testminer/#microsoft), [Apple](https://andrehora.github.io/testminer/#apple), [Facebook](https://andrehora.github.io/testminer/#facebook), [Netflix](https://andrehora.github.io/testminer/#netflix), 
[GitHub](https://andrehora.github.io/testminer/#github), [Apache](https://andrehora.github.io/testminer/#apache), [HuggingFace](https://andrehora.github.io/testminer/#huggingface)

## Passo 2: Explorar o repositório selecionado

Busque o repositório escolhido no [TestMiner](https://andrehora.github.io/testminer) e analise os dados de teste gerados pela ferramenta.

## Passo 3: Explicar uma prática de teste

Escolha uma prática ou dado de teste relevante e explique com suas próprias palavras.

---

## Instruções de entrega

1. Faça um `fork` deste repositório (saiba mais sobre forks [aqui](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)).
2. Responda às questões abaixo diretamente neste arquivo `README.md` do seu fork. Pode adicionar imagens para enriquecer sua explicação.
3. No Moodle, submeta apenas a URL do seu fork.

---

## Respostas

Repositório: [fastapi](https://github.com/fastapi/fastapi)

URL TestMiner: [TestMiner fastapi](https://andrehora.github.io/testminer/#fastapi/fastapi)

Explicação: O repositório possui 370 testes padrões (unitários ou de integração), 95 test helpers, mas a maioria é de indicador `__init__.py`, 13 benchmarks, 2 CI tests e 1 teste Smoke. Os nomes de cada arquivo teste é intuitivo do que está sendo testado ali, só não há uma separação clara de testes unitários de testes de integração. Há uso constante de fixture e de parametrizing testes, como nos exemplos abaixo, e não achei uso de mock ou stubb nos testes.

```python
@pytest.fixture(
    name="client",
    params=[
        pytest.param("tutorial002_py310", marks=needs_py310),
        pytest.param("tutorial002_an_py310", marks=needs_py310),
    ],
)

@pytest.mark.parametrize(
    "path,expected_status,expected_response",
    [
        ("/items/", 200, [{"name": "Foo", "price": 42}]),
        ("/users/", 200, [{"username": "johndoe"}]),
        ("/elements/", 200, [{"item_id": "Foo"}]),
    ],
)
```

Há também muito testes voltados para exceções, verificando explicitamente que um erro é esperado quando executa uma determinada ação. Interessante a se notar é a documentação de alguns testes em diferentes linguagens (chines, ingles, portugues, etc) para entendimento geral do público.



