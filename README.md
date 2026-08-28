# teste_llm_judge

## O que foi implementado neste desafio

Além do bot base e do guia de instalação fornecidos pelo professor (ver `GUIA_INSTALACAO.md`), este repositório inclui:

- **Golden dataset** (`golden_dataset.json`) com 14 casos, cobrindo as 4 categorias avaliadas: consulta direta, recomendação por perfil, fora de escopo e adversarial.
- **Suíte de testes** em `test_cosmetic_bot.py` + `conftest.py`, usando `pytest.mark.parametrize` para rodar os 14 casos do dataset e uma fixture de sessão para instanciar o juiz uma única vez por execução.
- **`prompt.txt` corrigido** a partir dos achados da sessão exploratória (ver `RELATORIO TESTES EXPLORATÓRIOS.md`), endereçando os principais problemas identificados (alucinações de atributo/produto, ausência de recomendação de dermatologista, falhas de recusa em perguntas fora de escopo).

## Como rodar a suíte de testes

1. Ative o ambiente virtual:

```powershell
# Windows (PowerShell)
.venv\Scripts\Activate.ps1
```

```bash
# Linux/macOS
source .venv/bin/activate
```

2. Configure as variáveis de ambiente necessárias:

```powershell
$env:GEMINI_API_KEY = "sua-chave"   # gerada em https://aistudio.google.com
$env:JUIZ_PROVIDER = "gemini"
$env:JUIZ_MODEL = "gemini-3.5-flash-lite"
```

3. Rode a suíte completa:

```bash
deepeval test run test_cosmetic_bot.py
```

Para rodar apenas um subconjunto de casos, use a flag `-k` do pytest com o id do caso, por exemplo:

```bash
deepeval test run test_cosmetic_bot.py -k "consulta_01"
```

## Dataset e relatório

- O golden dataset usado pela suíte está em `golden_dataset.json`, na raiz do projeto.
- O relatório final da avaliação está em `relatorio_final.txt` (ou no documento Word gerado a partir dele, conforme entregável do desafio).

## Segurança e credenciais

Nenhuma chave de API fica no código-fonte. `GEMINI_API_KEY` é lida a partir de variável de ambiente da sessão do terminal — configure-a localmente antes de rodar os testes e nunca a comite no repositório.
