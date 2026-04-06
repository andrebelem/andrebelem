# Guia de Atualização: Métricas Acadêmicas

Este diretório contém os resultados das métricas do Google Scholar, gerados através do utilitário ([`bibliometrics`](https://github.com/cicirello/bibliometrics)). Devido a restrições de segurança (Erro 403 Forbidden) impostas pelo Google aos servidores do GitHub Actions, a atualização automática foi substituída pelo processo manual local.

## Configuração do Ambiente

Certifique-se de estar na raiz do repositório antes de executar os comandos.

- Criar o Ambiente Virtual (Apenas na primeira vez)
`python -m venv venv`

- Ativar o Ambiente
Windows (PowerShell): `.\venv\Scripts\activate`
Linux/macOS: `source venv/bin/activate`

- Instalar Dependências (caso não tenha feito)
`pip install bibliometrics`

## Como Atualizar as Métricas

Com o ambiente virtual (venv) devidamente ativado, siga os passos:

- O comando abaixo lerá o arquivo .bibliometrics.config.json na raiz, que deve conter o seu scholarID:
`python -m bibliometrics`
- Confirme se os arquivos `scholar.svg` e `bibliometrics.json` foram atualizados neste diretório.

- Subir para o GitHub
```
git add academic_metrics/
git commit -m "update: métricas do Google Scholar"
git push
```

## Detalhes da Configuração

As métricas suportadas e geradas incluem:
- Total de citações, h-index, i10-index e g-index.
- m-quotient, e-index, r-index e a-index.
- O utilitário respeita o robots.txt do Google Scholar, limitando a análise à primeira página do perfil, o que corresponde a até 100 publicações.
- O arquivo de configuração `.bibliometrics.config.json` deve conter o `scholarID` do perfil do Google Scholar, o caminho para o arquivo JSON de saída e a string do User-Agent para evitar bloqueios.