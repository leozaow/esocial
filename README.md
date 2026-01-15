# eSocial • Editores (S-1202 / S-1210)

Este repositório reúne duas ferramentas simples (e bem práticas) para **editar arquivos JSON de eventos do eSocial**, diretamente no navegador, sem backend.

A ideia aqui é agilizar o saneamento/conferência de arquivos antes da transmissão, mantendo uma abordagem conservadora (evitar mudanças desnecessárias e preservar integridade do conteúdo).

## Como usar (rápido)

1. Abra o GitHub Pages e escolha o editor:
   - **S-1202**: `esocial/S-1202.html`
   - **S-1210**: `esocial/S-1210.html`
2. Clique em **Carregar Arquivo JSON** e selecione o arquivo do evento.
3. Use as ferramentas do editor conforme a necessidade.
4. Clique em **Baixar Edição** e salve o arquivo ajustado.

Observação: os arquivos são processados **localmente** no navegador.

## O que cada editor faz

### Editor S-1202 (Remuneração RPPS)
Ferramentas principais:
- Filtrar/excluir trabalhadores por CPF.
- Analisar matrículas via CSV.
- Informar **Categoria e Estabelecimento** (preenchendo apenas placeholders por padrão).
- Mesclar rubricas por `ideDmDev`.
- Ajustar pagamentos negativos e verificar RRA.

Estrutura esperada (raiz do JSON):
```json
{
  "s1202RemuTrabRPPSGroup": {
    "s1202RemuTrabRPPS": []
  }
}
```

Notas técnicas:
- O carregamento faz um reparo mínimo quando necessário (ex.: BOM e vírgula sobrando no final), apenas para permitir a leitura.
- No download, marcações internas como `_selected` são removidas automaticamente.

### Editor S-1210 (Pagamentos / IR)
Ferramentas principais:
- Excluir eventos por lista de CPFs.
- Sincronizar dependentes (InfoDep) a partir de uma base.
- Sincronizar líquidos (`vrLiq`) e `ideDmDev` a partir de uma base.
- Busca/seleção em massa para acelerar revisões.

Estrutura esperada (raiz do JSON):
```json
{
  "s1210PagtoRendTrabGroup": {
    "s1210PagtoRendTrab": []
  }
}
```

Nota de integridade:
- O editor mantém uma lógica de salvamento conservadora (aplica “patch” no que foi editado e evita injetar estruturas vazias automaticamente).

## Aviso
Estas ferramentas não substituem validação oficial do eSocial nem revisão técnica/jurídica do conteúdo. Use com critério, valide o arquivo resultante e mantenha rastreabilidade/auditoria do que foi alterado.
