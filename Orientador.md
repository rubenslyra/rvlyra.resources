# Passo a Passo para Criar e Empacotar o Projeto "rvlyra.resources" - Versão 0.1.0

## RerÊncias:
- [ ] [packing-a-license-expression-or-a-license-file](https://learn.microsoft.com/pt-br/nuget/reference/msbuild-targets#packing-a-license-expression-or-a-license-file)
- [ ] [nuspec#license](https://learn.microsoft.com/pt-br/nuget/reference/nuspec#license)
- [ ] [criadno o readme corretamente](https://learn.microsoft.com/pt-br/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

**1. Inicialização do Projeto:**
   - Abra o terminal e navegue até o diretório onde deseja criar o projeto.
   - Execute o comando para criar um novo projeto de biblioteca de classes:
     ```bash
     dotnet new classlib -n rvlyra.resources -o rvlyra.resources
     ```
   - Entre no diretório do projeto:
     ```bash
     cd rvlyra.resources
     ```

**2. Adicionar Estrutura de Pastas:**
   - Crie uma estrutura de pastas para organizar seus recursos multilíngues:
     ```bash
     mkdir Resources
     mkdir Resources/pt-BR
     mkdir Resources/en-US
     mkdir Resources/es-ES
     ```

**3. Adicionar Arquivos de Resources:**
   - Crie arquivos `.resx` para cada idioma na pasta correspondente (por exemplo, `Resources/pt-BR/Mensagens.resx`).
   - Abra os arquivos no VS Code ou no editor de sua escolha e adicione mensagens conforme necessário.

**4. Definir Metadados do Projeto:**
   - Edite o arquivo `rvlyra.resources.csproj` para incluir metadados relevantes.
     Exemplo:
     ```xml
     <Project Sdk="Microsoft.NET.Sdk">

       <PropertyGroup>
         <TargetFramework>netstandard2.0</TargetFramework>
         <PackageId>rvlyra.resources</PackageId>
         <Version>0.1.0</Version>
         <Authors>Ruben Lyra</Authors>
         <Description>Conjunto de recursos multilíngues para aplicativos .NET.</Description>
         <!-- Outras propriedades e metadados conforme necessário -->
       </PropertyGroup>

     </Project>
     ```

**5. Estruturar Código:**
   - Crie uma classe estática para acessar as mensagens. Exemplo:
     ```csharp
     // Arquivo Mensagens.cs
     namespace rvlyra.resources
     {
         public static class Mensagens
         {
             // Implemente métodos ou propriedades para acessar mensagens.
         }
     }
     ```

**6. Empacotar e Publicar Localmente (Opcional):**
   - Execute o comando para empacotar o projeto:
     ```bash
     dotnet pack -c Release
     ```
   - Instale localmente para testar:
     ```bash
     dotnet nuget add source ./bin/Release/
     dotnet add package rvlyra.resources --version 0.1.0
     ```

**7. Documentação e README.md:**
   - Crie ou atualize o arquivo `README.md` com informações sobre instalação, uso e contribuições.
   - Adicione informações sobre o suporte a idiomas e versões do .NET.

**8. Subir para o GitHub:**
   - Crie um repositório no GitHub.
   - Adicione os arquivos do projeto ao repositório:
     ```bash
     git init
     git add .
     git commit -m "Inicializando projeto rvlyra.resources"
     git remote add origin URL_DO_SEU_REPOSITORIO
     git push -u origin master
     ```

**9. Publicar no NuGet:**
   - Crie uma conta no NuGet (se já não tiver).
   - Execute o comando para enviar o pacote:
     ```bash
     dotnet nuget push ./bin/Release/rvlyra.resources.0.1.0.nupkg -k SUA_CHAVE_API_NUGET -s https://api.nuget.org/v3/index.json
     ```
   - Certifique-se de substituir `SUA_CHAVE_API_NUGET` pela sua chave de API NuGet.

**10. Notas da Versão 0.1.0:**
   - Documente as alterações e melhorias na primeira versão.
   - Atualize o arquivo `README.md` com as notas da versão.

Este passo a passo deve ajudar a criar, empacotar e publicar a versão 0.1.0 do seu projeto "rvlyra.resources". Se tiver dúvidas ou precisar de mais orientações, estou à disposição!


----

# Testes 

Para facilitar a criação de recursos usando a CLI do .NET e ajustar os formatos para o VS Code reconhecer, vamos usar o comando `dotnet resource`.

**1. Criar Recursos com o Comando `dotnet resource`:**
```bash
dotnet resource generate -t "Mensagens" -l pt-BR
dotnet resource generate -t "Messages" -l en-US
dotnet resource generate -t "Mensajes" -l es-ES
```

Isso criará automaticamente arquivos `.resx` com os nomes corretos e adicionará as entradas iniciais para cada idioma. Os arquivos gerados estarão na pasta `Resources` com os seguintes nomes:
- `Mensagens.pt-BR.resx`
- `Messages.en-US.resx`
- `Mensajes.es-ES.resx`

**2. Estrutura de Arquivos após a Execução:**
```bash
rvlyra.resources
|-- Resources
|   |-- pt-BR
|   |   `-- Mensagens.pt-BR.resx
|   |-- en-US
|   |   `-- Messages.en-US.resx
|   |-- es-ES
|       `-- Mensajes.es-ES.resx
|-- rvlyra.resources.csproj
|-- Mensagens.cs
|-- Messages.cs
```

**3. Adicionar Testes:**
```bash
dotnet new xunit -n rvlyra.resources.tests
cd rvlyra.resources.tests
dotnet add reference ../rvlyra.resources/rvlyra.resources.csproj
```

Crie arquivos de teste em `rvlyra.resources.tests` para garantir que os recursos estejam sendo carregados corretamente e as mensagens estejam acessíveis.

**Exemplo de Teste (usando Xunit):**
```csharp
// Arquivo: rvlyra.resources.tests/MensagensTests.cs
using Xunit;
using rvlyra.resources;

public class MensagensTests
{
    [Fact]
    public void DeveRetornarBoasVindasEmPortugues()
    {
        var mensagem = Mensagens.BoasVindas;
        Assert.Equal("Bem-vindo ao nosso sistema!", mensagem);
    }

    [Fact]
    public void ShouldReturnWelcomeInEnglish()
    {
        var message = Messages.Welcome;
        Assert.Equal("Welcome to our system!", message);
    }

    [Fact]
    public void DeberiaRetornarBienvenidoEnEspanol()
    {
        var mensaje = Mensajes.Bienvenido;
        Assert.Equal("Bienvenido a nuestro sistema!", mensaje);
    }
}
```

**4. Executar Testes:**
```bash
dotnet test
```

Isso executará os testes, garantindo que os recursos estejam sendo gerados corretamente e que as mensagens estejam acessíveis em cada idioma.

Essas etapas devem ajudar a criar, testar e organizar recursos multilíngues para seu projeto. Se precisar de mais assistência ou ajustes, estou à disposição!
