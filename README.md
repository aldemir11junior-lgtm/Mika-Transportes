# Painel Operacional — Transportadora XYZ (versão Streamlit)

Aplicação interna, em **um único arquivo Python** (`app.py`), usando **Streamlit**.
Todos os dados (usuários, motoristas, veículos, viagens) ficam salvos localmente em
**`cache.pkl`** — um arquivo binário criado automaticamente na primeira execução.

## Como rodar

```
pip install -r requirements.txt
streamlit run app.py
```

O navegador abre automaticamente em **http://localhost:8501**.

Login de exemplo (criado sozinho na primeira execução):

| Perfil       | E-mail                | Senha  |
|--------------|------------------------|--------|
| Gerente      | gerente@xyz.com        | 123456 |
| Operacional  | operacional@xyz.com    | 123456 |

## Onde ficam os dados

Tudo é salvo em **`cache.pkl`**, na mesma pasta do `app.py`. É um arquivo `pickle` do
Python — não abra/edite ele manualmente, apenas deixe o app cuidar disso.

- Para **resetar tudo** (voltar aos dados de exemplo): feche o Streamlit e apague o
  arquivo `cache.pkl`. Ele é recriado do zero na próxima execução.
- Para **fazer backup**: basta copiar o arquivo `cache.pkl` para outro lugar.
- **Importante**: como os dados ficam num arquivo local, use isso apenas rodando na
  mesma máquina (ou compartilhando a pasta em rede). Não é recomendado para múltiplos
  usuários gravando ao mesmo tempo em instâncias separadas — para esse cenário, o ideal
  seria voltar a um banco de dados de verdade (Postgres, por exemplo).

## O que tem pronto

- ✅ Login (sem área pública — tudo exige autenticação)
- ✅ Dois perfis: `operacional` e `gerente` (gerente também gerencia usuários e pode excluir viagens)
- ✅ Dashboard com gráficos (Faturamento x Custo, Volume por mês, Custo médio/KM)
- ✅ CRUD de Viagens (criar, listar, editar, excluir)
- ✅ Cadastro de Motoristas e Veículos
- ✅ CRUD de Usuários (criar, editar, excluir — restrito ao perfil gerente)
- ✅ Exportação da listagem de viagens em CSV, Excel e PDF

## Estrutura

```
TransportesStreamlit/
├── app.py              # TODO o sistema: dados, telas, lógica — um único arquivo
├── requirements.txt
├── cache.pkl            # criado automaticamente na 1ª execução (não subir pro Git)
└── README.md
```

## Próximos passos sugeridos

- Trocar as senhas de exemplo antes de usar com a equipe de verdade.
- Se o uso crescer (muita gente lançando ao mesmo tempo), migrar `cache.pkl` para um
  banco de dados real evita conflitos de escrita simultânea.
- Publicar com Streamlit Community Cloud (share.streamlit.io) para acesso via link,
  conectando direto no repositório do GitHub.
