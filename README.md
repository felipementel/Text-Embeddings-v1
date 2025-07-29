# 🚀 Azure OpenAI Text Embeddings

Este projeto demonstra como usar o Azure OpenAI para gerar embeddings de texto e calcular similaridade semântica entre palavras e frases.

## 📝 Descrição

O projeto utiliza a API do Azure OpenAI para converter texto em representações vetoriais (embeddings) e implementa cálculos de similaridade cosseno para comparar a semelhança semântica entre diferentes textos.

## 🛠️ Tecnologias Utilizadas

- **Python 3.x**
- **Azure OpenAI API** - Para geração de embeddings
- **NumPy** - Para cálculos matemáticos
- **OpenAI Python SDK** - Cliente oficial para Azure OpenAI
- **python-dotenv** - Para gerenciamento de variáveis de ambiente
- **Matplotlib, Plotly, Scikit-learn, Pandas** - Para análise e visualização de dados

## 📋 Pré-requisitos

### Recursos Azure
- Uma conta Azure ativa
- Um recurso Azure OpenAI criado
- Um modelo de embeddings deployado (ex: text-embedding-ada-002)

### Python
- Python 3.7+
- pip (gerenciador de pacotes Python)

## ⚙️ Configuração

### 1. Clone o repositório
```bash
git clone <url-do-repositorio>
cd text-embeeding
```

### 2. Configure as variáveis de ambiente
Crie um arquivo `.env` na raiz do projeto com as seguintes variáveis:

```env
AZURE_OPENAI_API_KEY=sua_chave_api_aqui
AZURE_OPENAI_ENDPOINT=https://seu-recurso.openai.azure.com/
AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT=nome_do_seu_deployment
```

### 3. Instale as dependências
```bash
pip install -r requirements.txt
```

### 4. Configuração adicional para Windows
Para suporte a caminhos longos no Windows, execute no PowerShell como administrador:
```powershell
New-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```

## 🚀 Uso

### Executando o Notebook

1. Abra o arquivo `aoai-assignment.ipynb` no Jupyter Notebook ou VS Code
2. Execute as células sequencialmente

### Funcionalidades Principais

#### 1. **Geração de Embeddings**
```python
text = 'Eu quero entender mais sobre OpenTelemetry'
embedding = client.embeddings.create(input=[text], model=model).data[0].embedding
```

#### 2. **Cálculo de Similaridade Cosseno**
```python
def cosine_similarity(a, b):
    return np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b))
```

#### 3. **Comparação de Palavras**
O projeto demonstra como comparar a similaridade entre diferentes palavras:
- `Carro` vs `Milho` (baixa similaridade)
- `Carro` vs `Retrato` (baixa similaridade)
- `Carro` vs `stick` (baixa similaridade)

## 📊 Exemplo de Resultados

Ao executar o código, você verá resultados similares a:

```
1.0000000000000000    # palavra vs ela mesma (idêntico)
0.2345678901234567    # carro vs milho (baixa similaridade)
0.1234567890123456    # carro vs retrato (baixa similaridade)
0.0987654321098765    # carro vs stick (baixa similaridade)
```

## 🏗️ Estrutura do Projeto

```
text-embeeding/
├── aoai-assignment.ipynb    # Notebook principal com exemplos
├── README.md               # Este arquivo
├── requirements.txt        # Dependências Python
└── .env                   # Variáveis de ambiente (não incluído no git)
```

## 🔧 Detalhes Técnicos

### API Version
O projeto utiliza a versão `2023-05-15` da API do Azure OpenAI.

### Embeddings
- Os embeddings são vetores de alta dimensionalidade que representam o significado semântico do texto
- Textos com significados similares terão embeddings próximos no espaço vetorial
- A similaridade cosseno varia de -1 a 1, onde 1 indica máxima similaridade

### Similaridade Cosseno
A fórmula utilizada é:
```
cos(θ) = (A · B) / (||A|| × ||B||)
```

Onde:
- A e B são os vetores de embeddings
- · representa o produto escalar
- ||A|| e ||B|| são as normas dos vetores

## 💡 Exemplos de Uso

### Análise de Similaridade Semântica
O notebook demonstra como diferentes palavras se relacionam semanticamente:

1. **Instalação de dependências**: Instala todas as bibliotecas necessárias
2. **Configuração do cliente**: Conecta com o Azure OpenAI usando variáveis de ambiente
3. **Geração de embeddings**: Converte texto em português para vetores numéricos
4. **Comparação de similaridade**: Calcula quão similares são diferentes conceitos

## 🚨 Importante

### Segurança
- **Nunca** commite o arquivo `.env` com suas chaves de API
- Mantenha suas credenciais Azure seguras
- Use diferentes ambientes para desenvolvimento e produção

### Custos
- O uso da API do Azure OpenAI gera custos
- Monitore o uso através do portal Azure
- Considere implementar limites de taxa para controlar gastos

## 🤝 Contribuindo

1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/nova-funcionalidade`)
3. Commit suas mudanças (`git commit -am 'Adiciona nova funcionalidade'`)
4. Push para a branch (`git push origin feature/nova-funcionalidade`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

## 📞 Suporte

Para dúvidas ou suporte:
- Abra uma issue no GitHub
- Consulte a [documentação oficial do Azure OpenAI](https://docs.microsoft.com/azure/cognitive-services/openai/)

## 🔗 Links Úteis

- [Azure OpenAI Documentation](https://docs.microsoft.com/azure/cognitive-services/openai/)
- [OpenAI Python SDK](https://github.com/openai/openai-python)
- [Text Embeddings Guide](https://platform.openai.com/docs/guides/embeddings)
- [Azure OpenAI Pricing](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/)

---

**Nota**: Este projeto é para fins educacionais e demonstração das capacidades do Azure OpenAI para processamento de linguagem natural.
