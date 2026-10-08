<p align="center">
  <img src="mobile/assets/images/autoguardia_logo.png" alt="AUTOGUARDIA" width="280">
</p>

# AUTOGUARDIA — CarGPT

Aplicativo de gestão e acompanhamento automotivo desenvolvido em **Flutter**, com foco em Android. Reúne garagem virtual, histórico de manutenção, abastecimentos, relatórios de gastos, ferramentas de cálculo, telemetria OBD2 e um assistente de inteligência artificial em português brasileiro.

O objetivo é ajudar o motorista a organizar os cuidados com o veículo, acompanhar os custos de uso e entender as informações fornecidas pela central eletrônica.

**Status:** projeto em desenvolvimento, em versão beta. O nome do produto é AUTOGUARDIA; o repositório e alguns componentes utilizam o nome CarGPT.

## Funcionalidades

### Conta e perfil

- Cadastro e login com e-mail e senha pelo Supabase Auth.
- Tratamento da confirmação de e-mail quando habilitada no projeto Supabase.
- Opção de lembrar o login no aparelho.
- Edição de nome e sobrenome, com identificação personalizada na tela inicial.
- Encerramento da sessão pelo aplicativo.
- Exibição da versão instalada e consulta de atualizações disponíveis.

### Tela inicial

Apresenta a identificação do usuário e atalhos para **Minha garagem**, **Diagnóstico OBD2**, **Assistente IA**, **Relatórios**, **Ferramentas** e **Meu perfil**.

### Minha garagem

Permite cadastrar e gerenciar os veículos da conta.

- Cadastro de marca, modelo, ano, motorização e quilometragem atual.
- Seleção de marcas e modelos do catálogo local, com preenchimento manual para outras opções.
- Listagem, edição e exclusão de veículos.
- Atualização manual do hodômetro.
- Tela individual com resumo de gastos no mês, gastos acumulados e situação das manutenções.
- Atalhos para registrar serviços, consultar o histórico, acompanhar abastecimentos e abrir o calendário.

### Manutenções e vida útil das peças

Organiza os serviços realizados e os intervalos previstos para as próximas trocas.

- Cadastro de serviço realizado, peça ou item trocado, data, custo, quilometragem e observações.
- Categorias como óleo e filtros, revisão, freios, suspensão, pneus, motor, transmissão, arrefecimento, elétrica, ar-condicionado e funilaria.
- Opção **Outros** para descrever serviços e peças personalizados.
- Definição opcional de vida útil em meses e/ou quilômetros.
- Cálculo da próxima troca a partir da data e do hodômetro registrados no serviço.
- Identificação de serviços vencidos e acompanhamento das próximas revisões no painel do veículo.
- Ação para registrar uma nova troca a partir de uma manutenção acompanhada.
- Consulta, edição e exclusão dos registros no histórico.

Os formulários utilizam rótulos fixos, pontuação brasileira e limites de entrada. O custo de manutenção aceita até **R$ 999.999,99**, e a quilometragem até **9.999.999 km**.

### Notas fiscais e documentos

- Anexo de fotos e PDFs aos registros de manutenção.
- Formatos aceitos: JPEG, PNG, WebP e PDF, com limite de **10 MB** por arquivo.
- Visualização do comprovante junto aos detalhes do serviço, incluindo leitura de PDFs no aplicativo.
- Remoção ou substituição do anexo ao editar a manutenção.
- Armazenamento no bucket privado `maintenance-invoices`, com regras de acesso por usuário.

### Calendário de manutenção

- Navegação entre meses.
- Consulta dos serviços registrados e das próximas revisões com data calculada.
- Filtros por manutenção, documentos e gastos.
- Exibição da data, descrição e quilometragem associadas aos eventos.

As previsões dependem dos intervalos cadastrados. O acompanhamento por quilometragem utiliza o hodômetro informado pelo usuário.

### Abastecimentos e consumo

- Registro de posto, data, combustível, litros, preço por litro, valor total e quilometragem.
- Marcação de abastecimento com tanque cheio.
- Histórico de abastecimentos por veículo.
- Indicadores e gráficos de consumo e custo por quilômetro, quando há dados suficientes.

O consumo é estimado a partir dos registros de abastecimento e hodômetro. A marcação de tanque cheio é utilizada nos cálculos dos intervalos de consumo.

### Gastos e relatórios

Reúne informações de manutenção e combustível para acompanhar o custo de uso do veículo.

- Detalhamento dos gastos do mês e dos gastos acumulados.
- Seleção de veículo e ano nos relatórios.
- Resumo de gastos com manutenção, combustível e total do período.
- Quantidade de manutenções e estimativa de distância percorrida.
- Gráficos mensais de gastos totais, combustível e manutenção.
- Gráficos de custo por quilômetro e consumo médio.

Os indicadores de distância, consumo e custo por quilômetro dependem da quantidade e da consistência dos registros disponíveis.

### Ferramentas automotivas

Calculadoras com atualização dos resultados conforme o preenchimento dos campos.

| Ferramenta | Função |
| --- | --- |
| Planejar viagem | Calcula combustível necessário e custo estimado usando distância, consumo médio e preço do combustível; origem e destino identificam a viagem. |
| Consumo médio | Calcula km/L usando distância percorrida e litros consumidos. |
| Custo por quilômetro | Calcula R$/km a partir do gasto e da distância. |
| Estimativa de autonomia | Calcula a distância estimada com o combustível disponível e o consumo médio. |
| Conversão de pressão | Converte valores entre psi e bar. |
| Conversão de volume | Converte litros e galões americanos (US). |

A distância rodoviária deve ser informada pelo usuário, a partir de seu aplicativo de mapas. Os campos possuem limites, rótulos fixos e formatação numérica no padrão brasileiro.

### Conexão e painel OBD2

- Conexão com adaptadores compatíveis com ELM327 por **Bluetooth clássico**, no Android.
- Listagem de dispositivos Bluetooth pareados e solicitação das permissões necessárias.
- Inicialização da comunicação com o adaptador e descoberta dos PIDs suportados pelo veículo.
- Leitura periódica dos sensores disponibilizados pela central eletrônica.
- Identificação de parâmetros não suportados.

#### Painel personalizável

- Seleção de **Top 4** ou **Top 6** medidores favoritos, salva localmente no aparelho.
- Cards com ponteiros animados, leitura numérica e mini gráfico dos últimos 30 segundos.
- Lista avançada para consultar todos os parâmetros exibidos pelo aplicativo.
- Indicação de leituras sem atualização recente.
- Respeito à preferência do sistema para reduzir animações.

#### Detalhes de cada sensor

Ao tocar em um card ou item da lista, uma tela específica apresenta:

- Leitura ampliada, atualizada durante a sessão.
- Gráfico dos últimos 30 segundos, com escala e marcações de tempo.
- Mínimo, média, máximo e quantidade de amostras na janela exibida.
- Identificação do parâmetro, unidade e escala visual do medidor.
- Limites de alerta configurados, quando aplicáveis.
- Explicação do significado do sensor.

Parâmetros que representam estados ou descrições são exibidos como texto, sem criar um gráfico numérico. A conexão permanece ativa ao abrir e fechar os detalhes.

#### Parâmetros acompanhados

| Grupo | Leituras |
| --- | --- |
| Motor e condução | RPM, velocidade, carga do motor, carga absoluta, posição do acelerador e tempo desde a partida. |
| Temperaturas | Líquido de arrefecimento, ar de admissão, ambiente e catalisador. |
| Admissão e ignição | Pressão absoluta do coletor, boost calculado e avanço da ignição. |
| Combustível | Estado do sistema, ajustes de curto e longo prazo, tipo de combustível e percentual de etanol. |
| Sensores de oxigênio | Localização dos sensores e tensões dos sensores B1S1 a B2S4, conforme suporte. |
| Sistema elétrico | Tensão medida pelo módulo de controle. |

O boost é estimado pela diferença entre a pressão do coletor e a pressão barométrica, quando ambas estão disponíveis.

#### Alertas visuais

| Parâmetro | Amarelo | Vermelho |
| --- | --- | --- |
| Temperatura do arrefecimento | Acima de 100 °C e abaixo de 110 °C. | A partir de 110 °C. |
| Tensão do módulo | Abaixo de 11,8 V e a partir de 11,5 V. | Abaixo de 11,5 V. |

Os cards do painel pulsam em vermelho nas condições críticas, quando as animações estão habilitadas. Esses limites são referências configuradas no app; a interpretação depende do veículo e das condições de funcionamento.

### Códigos de falha e análise OBD2

- Consulta dos códigos de falha armazenados na ECU.
- Catálogo local com explicações, sistema afetado, possíveis causas e próximos passos para códigos catalogados.
- Envio de um código ao assistente IA para obter uma explicação em português.
- Envio de um resumo das leituras do painel para análise pelo assistente.
- Comando para apagar códigos da ECU, com confirmação antes do envio.

### Modo de demonstração OBD2

Permite testar a interface sem um veículo conectado, utilizando leituras simuladas e um código de falha de exemplo.

Para habilitar, abra a tela **Conectar meu carro**, toque **sete vezes no título** e confirme a ativação do modo de testes. Em seguida, use **Testar sem conectar ao carro**. A preferência fica salva no aparelho e pode ser desativada pelo mesmo caminho.

### Assistente IA

- Chat automotivo em português brasileiro.
- Seleção de um veículo da garagem para contextualizar as respostas.
- Uso dos dados do veículo e das dez manutenções mais recentes como contexto, quando um veículo é selecionado.
- Histórico armazenado no Supabase, com recuperação das últimas 100 mensagens ao abrir o chat.
- Integração com Google Gemini por uma Supabase Edge Function.
- Novas tentativas e modelo alternativo configurável para indisponibilidade temporária do provedor.
- Acesso a partir dos atalhos de diagnóstico, códigos de falha e análise das leituras OBD2.

### Atualizações sem loja

- Versão instalada disponível na área de perfil.
- Botão **Buscar atualização**, com consulta à tabela `app_releases` no Supabase.
- Comparação pelo número de compilação do aplicativo.
- Exibição da versão disponível e das notas da atualização.
- Abertura do link do APK no navegador, seguida da instalação confirmada pelo usuário no Android.

O APK pode ser hospedado em uma Release pública do GitHub ou em outro endereço HTTPS acessível. Consulte o [guia de publicação de atualizações](docs/atualizacoes-android.md).

## Tecnologias e arquitetura

| Camada | Tecnologias |
| --- | --- |
| Aplicativo | Flutter e Dart. |
| Autenticação e banco | Supabase Auth e PostgreSQL. |
| Documentos | Supabase Storage, `file_picker` e `pdfrx`. |
| Assistente | Supabase Edge Functions, TypeScript/Deno e Google Gemini. |
| OBD2 | `flutter_bluetooth_serial`, com pacote local em `mobile/packages/`. |
| Preferências locais | `shared_preferences`. |
| Formatação | `intl` e formatadores brasileiros do projeto. |
| Versão e downloads | `package_info_plus` e `url_launcher`. |

O aplicativo utiliza o Supabase diretamente para autenticação, veículos, manutenções, abastecimentos e histórico do chat. A chave da IA permanece no servidor, na Edge Function.

O diretório `backend/` contém um **protótipo separado** em Python/FastAPI, com SQLAlchemy, SQLite e autenticação própria. Ele não é necessário para executar os fluxos atuais do aplicativo Flutter.

## Estrutura do projeto

```text
CarGPT/
├── mobile/
│   ├── lib/
│   │   ├── core/              # Modelos, serviços, OBD2, formatadores e widgets
│   │   └── features/
│   │       ├── auth/          # Login, cadastro, perfil e atualizações
│   │       ├── home/          # Tela inicial
│   │       ├── garage/        # Veículos, abastecimentos, calendário e relatórios
│   │       ├── maintenance/   # Serviços, histórico e comprovantes
│   │       ├── obd/           # Conexão, painel, sensores e códigos de falha
│   │       ├── chat/          # Assistente IA
│   │       └── tools/         # Calculadoras automotivas
│   ├── assets/               # Configuração local e imagens
│   ├── packages/             # Dependências locais
│   └── test/                 # Testes Flutter
├── supabase/
│   ├── schema.sql            # Tabelas, políticas e Storage
│   ├── migrations/           # Migrações complementares
│   └── functions/cargpt-chat/ # Integração com Gemini
├── docs/                     # Guias do projeto
└── backend/                  # Protótipo Python independente
```

## Como executar

### Pré-requisitos

- Flutter com Dart compatível com o [pubspec.yaml](mobile/pubspec.yaml), que exige Dart `^3.12.0`.
- Android SDK e um dispositivo ou emulador Android para executar o aplicativo.
- Projeto Supabase configurado.
- Adaptador OBD2 Bluetooth clássico compatível, para leituras reais.
- Chave Google Gemini configurada no servidor, para utilizar o assistente.

### 1. Configurar o Supabase

No SQL Editor do projeto Supabase:

1. Execute [`supabase/schema.sql`](supabase/schema.sql) para configurar as tabelas, índices, políticas de acesso e o bucket de comprovantes.
2. Aplique as migrações de [`supabase/migrations/`](supabase/migrations/) em ordem cronológica. Elas incluem o histórico de chat e a tabela de versões do app.
3. Configure a confirmação de e-mail no Supabase Auth conforme o fluxo de cadastro desejado.

Em um banco existente, confira a estrutura antes de executar os scripts. O uso de `create table if not exists` não adapta automaticamente tabelas antigas com colunas incompatíveis.

### 2. Configurar o aplicativo

Crie ou ajuste `mobile/assets/.env`:

```dotenv
SUPABASE_URL=https://SEU_PROJETO.supabase.co
SUPABASE_ANON_KEY=SUA_CHAVE_PUBLICA
```

Esse é o arquivo carregado pelo Flutter. As configurações do protótipo `backend/` são independentes.

Use somente a chave pública anon/publishable no app. Credenciais administrativas, `service_role` e `GEMINI_API_KEY` não devem ser incluídas no aplicativo nem publicadas no repositório.

### 3. Configurar o assistente

Publique [`supabase/functions/cargpt-chat/index.ts`](supabase/functions/cargpt-chat/index.ts) como a Edge Function `cargpt-chat` no mesmo projeto Supabase.

Configure os seguintes secrets no servidor:

| Variável | Uso |
| --- | --- |
| `GEMINI_API_KEY` | Chave de acesso ao Google Gemini; necessária para o chat. |
| `GEMINI_MODEL` | Opcional: modelo principal a utilizar, disponível para a chave configurada. |
| `GEMINI_FALLBACK_MODEL` | Opcional: modelo alternativo utilizado em caso de indisponibilidade temporária. |

A função também utiliza `SUPABASE_URL` do ambiente Supabase e exige uma sessão autenticada. A configuração de verificação JWT está em [`supabase/config.toml`](supabase/config.toml).

### 4. Instalar dependências e iniciar

Na raiz do repositório:

```powershell
cd mobile
flutter pub get
flutter run
```

Para utilizar OBD2 real, pareie o adaptador no Android, conceda as permissões solicitadas e selecione o dispositivo na tela de conexão. As leituras dependem da compatibilidade do veículo, do adaptador e dos PIDs disponíveis.

## Gerar o APK

Na pasta `mobile`:

```powershell
flutter build apk --release
```

O arquivo gerado fica em:

```text
mobile/build/app/outputs/flutter-apk/app-release.apk
```

A versão é definida em [`mobile/pubspec.yaml`](mobile/pubspec.yaml), no formato `versão+númeroDaCompilação`. Aumente o número da compilação a cada atualização distribuída.

A configuração Android atual utiliza assinatura de debug no build de release. A distribuição e as atualizações devem considerar a assinatura dos APKs já instalados. Os detalhes estão no [guia de atualizações Android](docs/atualizacoes-android.md).

## Testes

Os testes específicos dos recursos recentes cobrem atualização do app, alertas OBD2, histórico de sensores, navegação para detalhes, favoritos, formatação numérica e validação dos formulários.

Na pasta `mobile`:

```powershell
flutter test test/app_update_service_test.dart test/obd_dashboard_test.dart test/form_fields_test.dart
```

## Dados e acesso

- As tabelas utilizam políticas de Row Level Security (RLS) para restringir o acesso aos dados de cada usuário.
- Os comprovantes de manutenção ficam em Storage privado, com caminhos associados ao proprietário.
- A consulta de versões publicadas é permitida para usuários autenticados; a publicação é feita pela administração do projeto.
- Os dados do veículo selecionado, manutenções recentes e mensagens enviadas ao assistente são usados como contexto na integração com o provedor de IA.
- O histórico gráfico OBD2 é mantido em memória durante a sessão, em uma janela de 30 segundos; não é um registro permanente das viagens.

## Escopo e disponibilidade

O foco atual é Android. O repositório contém a estrutura Flutter para outras plataformas, mas a presença dessas pastas não garante suporte equivalente: a conexão OBD2 utiliza Bluetooth clássico no Android, e o fluxo de atualização por APK é específico dessa plataforma.

Garagem, registros e chat dependem da configuração e da conectividade com o Supabase. As calculadoras fazem os cálculos localmente; o assistente depende também da disponibilidade do Gemini.

As funções OBD2 e de IA ajudam a acompanhar informações e investigar sintomas. Uma leitura ou um código isolado não confirma a causa de uma falha; apagar códigos não corrige o problema mecânico.
