# Arquitetura - BASE

## Objetivo

Esse documento tem por objetivo principal organizar o processo de desenvolvimento, bem como as dependências e boas práticas a serem seguidas durante o desenvolvimento do software.

### Regras iniciais, limite e Análise

**Pontos a serem levados em consideração antes de introduzir uma nova feature:**

- Todo projeto precisará respeitar as regras de Lint escritas no pacote `flutterando-analysis`.
- Camadas globais devem ter um lugar específico na aplicação, por tanto, devem estar na pasta `shared`.

  _exemplo_:

  ```shell
  lib/
  ├── main.dart
  └── src
      └── shared
  ```

- Cada feature deverá ter sua própria pasta onde conterá todas as camadas necessárias para a execução dos casos de uso da feature.

  _exemplo_:

  ```shell
  lib/
  ├── main.dart
  └── src
      └── home
          └── home_page.dart
          └── home_store.dart
          └── widgets
              └── widgets usados na home page
  ```

- Todos os designs patterns usados no projeto devem estar listados na sessão “Design Patterns” desse documento, caso contrário será considerado implementação errônea e necessário refatoração.

- Packages e plugins novos só poderão ser usados nos projetos após avaliação e aprovação de toda equipe responsável pelo projeto. Sempre que possível passar o package/plugin por prova de conceito.

- Cada camada deve ter apenas **uma** responsabilidade.

- Não é permitido ter uma classe concreta como dependência de uma camada. Só será aceita coesão com classes abstratas ou interfaces. Com exceção da Store.

- Usar prioritariamente o `Theme.of(context)` do próprio flutter para personalizar os widgets nativos antes de criar componentes/widgets a parte, o mesmo vale para as cores usadas. Caso necessário que seja criado um aquivo dentro da pasta `shared/theme`.

### Entidades(_Models_)

Específico de cada projeto

### Casos de Uso

Específico de cada projeto

### Design Patterns

- Repository Pattern: Para acesso a API externa.
  Neste exemplo é feito o tratamento da API de login:

  ```shell
  lib/
  ├── main.dart
  └── src
      └── repository
          └── login_repository.dart
  ```

- Service Pattern: Para isolar trechos de códigos com outras responsabilidades.

  Neste exemplo é tratado o serviço de localização, onde ficará responsável por fazer a todo tratar as necessidades voltadas a essa funcionalidade:

  ```shell
  lib/
  ├── main.dart
  └── src
      └── services
          └── location
                └── location_service.dart
  ```

- Store: Guardar e mudar estados.
- Result: Trabalhar com retorno Múltiplo.
- Factory: Padrão onde as subclasses podem alterar os objetos de uma superclasse ao serem criados.

### Package externos (App)

- flutter_modular: Modularização de rotas e injeção de dependências.
- flutterando_analysis: lints do flutter implementados pela flutterando para melhor organização do código
- uno: Cliente HTTP.
- shared_preferences: persistência de dados locais.
- flutter_svg: tratamento e exibição de imagens svg
- result: Retorno múltiplo no formato Failure e Success.
- mobx: gerenciamento de estado com o uso de stores
- mobx_codegen: package que faz a geração dos arquivos necessários para o mobx funcionar
- build_runner: runner para executar a criação dos arquivos das outras dependências
- font_awesome_flutter: provedor de ícones
- iconsax: provedor de ícones
