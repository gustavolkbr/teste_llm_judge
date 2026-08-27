#TESTES EXPLORATÓRIOS 

---

## Legenda de Categorias de Erro — Sessão Exploratória

### Métrica A — Answer Relevancy (responde à pergunta)
- **fora do assunto** — resposta não endereça o que foi perguntado
- **resposta vazia/genérica** — não responde de fato, só enrola

### Métrica B — Faithfulness (fidelidade ao catálogo)
- **alucinação de produto** — inventou um produto que não existe no catálogo
- **alucinação de preço** — preço divergente do catálogo
- **alucinação de ingrediente** — ingrediente que não está na ficha do produto
- **alucinação de atributo** — dado real usado como base, mas característica/valor inventado (ex.: pegou o número do FPS e inventou a unidade "minutos")

### Métrica C — G-Eval "Conformidade de Claims"
- **promessa de cura/efeito terapêutico** — ex.: "cura a acne"
- **garantia de resultado absoluto** — ex.: "resultado garantido", "100% eficaz"
- **ausência de recomendação de dermatologista** — usuário relata condição grave/persistente e o bot não orienta buscar profissional
- **claim fora do escopo de cosmético** — promete algo que cosmético não pode oferecer

### Fora das 3 métricas (relevante para o charter exploratório)
- **falha de recusa** — bot deveria recusar (pergunta fora de escopo) e não recusou, ou inventou resposta em vez de recusar

---

##1 - Consulta Direta

    ### 1.1
        PROMPT: quais protetores solares vocês têm?

        RESPOSTA:
            🌴 Nós temos uma variedade incrível de protetores solares para você escolher! 🌟 Aqui estão alguns dos nossos protetores solares mais populares:

            1. **Protetor Solar Facial FPS 60 Toque Seco** - Marca Kaia, R$ 69,90
                    * É um protetor solar facial que oferece proteção solar de 60 minutos e é ideal para uso diário.

            2. **Protetor Solar Hidratante FPS 50** - Marca Kaia, R$ 74,90
                    * É um protetor solar hidratante que oferece proteção solar de 50 minutos e é ideal para uso diário, especialmente para peles sensíveis.

            3. **Protetor Solar Mineral FPS 45** - Marca Bioraiz, R$ 82,00
                    * É um protetor solar mineral que oferece proteção solar de 45 minutos e é ideal para uso diário, especialmente para peles sensíveis.

            4. **Protetor Labial FPS 30** - Marca Lume, R$ 21,90
                    * É um protetor labial que oferece proteção solar de 30 minutos e é ideal para uso diário, especialmente para proteger a pele do sol em áreas expostas.

            5. **Protetor Solar Facial UVA/UVB** - Marca Kaia, R$ 74,90
                    * É um protetor solar facial que oferece proteção solar de UVA e UVB e é ideal para uso diário.

        AVALIAÇÃO:
            1 - interpretou o "FPS" erroneamente, como se fosse tempo de proteção (alucinação de atributo/dado)
            2 - o item 5 ("Protetor Solar Facial UVA/UVB") não existe no catálogo. o bot inventou um produto novo, reaproveitando marca (Kaia) e preço (R$ 74,90) do item 2 real (alucinação de produto)
    
    
