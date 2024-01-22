# rvlyra.resources

[![NuGet](https://img.shields.io/nuget/v/rvlyra.resources.svg)](https://www.nuget.org/packages/rvlyra.resources/)

Conjunto de recursos multilíngues para aplicativos .NET.

## Instalação

Instale o pacote via NuGet Package Manager Console:

```bash
Install-Package rvlyra.resources -Version 1.0.0
```

Ou use o comando `dotnet`:

```bash
dotnet add package rvlyra.resources --version 1.0.0
```

## Utilização

1. Adicione uma referência ao pacote em seu projeto.
2. Acesse as mensagens de Resources conforme necessário.

Exemplo de utilização em C#:

```csharp
// Importe o namespace
using rvlyra.resources;

// Acesse mensagens de saudação em português
string saudacao = Mensagens.PtBR.SaudacaoManha;
```

## Suporte a Idiomas

O pacote oferece suporte aos seguintes idiomas:
- Português (pt-BR)
- Inglês (en-US)
- Espanhol (es-ES)

## Contribuições

Contribuições são bem-vindas! Se desejar adicionar suporte a mais idiomas ou corrigir algum problema, sinta-se à vontade para fazer um fork e enviar um pull request.

## Notas da Versão 1.0.0

- Mensagens iniciais em português, inglês e espanhol.
- Suporte a saudações, erros amigáveis, informações monetárias, geográficas e comerciais.
- Estrutura modular para fácil expansão.

Para obter informações detalhadas sobre as mensagens disponíveis, consulte os arquivos `.resx` na pasta `Resources`.

**Observação:** Este pacote é mantido por Ruben Lyra, Desenvolvedor e Analista de Sistemas.

Se precisar de mais assistência ou tiver sugestões, sinta-se à vontade para entrar em contato!
