# Worksflows Notion

Este repositório tem o intuito de abrigar worksflows do github que se conectam á plataforma **Notion** para
documentação,
logging e rastreabildiade de informação.

Como plataforma principal de concentração de informação do **Systock**, a automação dos processos listados acima se faz
necessário.

Abaixo está listado os workflows disponíveis, seu intuito e suas demais instruções de instalação.

### `notion-on-push-versionamento`

### Sobre:

No Systock, temos o controle da versão da aplicação, contemplada por um projeto frontend(vue.js) e um backend(laravel),
que traz consigo um histório do que foi adicionado/alterado, assim
como a versão resultante disso.

### Instalação:

1. Vamos criar alguns `secrets` em nosso repositório:

- Entre no repositório em questão, em: `Settings > Secrets and variables > Actions`
- Na aba `Repository secrets`, crie os seguintes secrets: `NOTION_API_KEY` `NOTION_DATABASE_ID`

Para saber mais como adquirir esses valores, acesse: `https://developers.notion.com/reference/intro`

2. Copie a estrutura presente aqui nos repositórios envolvidos:

```bash
/seu-repositorio
├── .github/
│ ├── workflows/
│   ├── notion-on-push-versionamento.yml
├── ...
```

3. Pronto, tudo já deve estar preparado para a automação. Agora, os commits seguindo a **estrutura esperada** gerarão um
   envio automático para o Notion:

### Estrutura esperada:

Desde que nosso commit siga a estrutura correta, as informações serão filtradas de forma automática e serão cadastradas.

```bash
git commit -m "Correção da função X que antes, quebrava a tela Y" -m ":tipo Bug :cliente EMPRESA X :zendesk https//:abc.zendesk.com/ticket/123 :notascs Solicitado pelo usuário beltrano";
```

O primeiro `-m` será inserido em 'Notas Internas', observação principal da versão. 

O segundo `-m` será usado para coletar as informações através dos parâmetros, que seram preenchidas em cada coluna.

| Parâmetro    | Valores          | Obrigatório |
|--------------|------------------|-------------|
| :tipo        | Bug ou Melhoria  | SIM         |
| :cliente     | string           | NAO         |
| :zendesk     | string           | NAO         |
| :notascs     | string           | NAO         |
| :responsavel | string           | NAO         |