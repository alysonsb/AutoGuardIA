# AUTOGUARDIA — CarGPT

Aplicativo de gestão e acompanhamento automotivo para **Android**. Reúne garagem virtual, histórico de manutenção, abastecimentos, relatórios de gastos, ferramentas de cálculo, telemetria OBD2 e um assistente de inteligência artificial em português brasileiro.

O objetivo é ajudar o motorista a organizar os cuidados com o veículo, acompanhar os custos de uso e entender as informações fornecidas pela central eletrônica.

**Status:** projeto em desenvolvimento, em versão beta.

## Sobre este repositório

Este repositório apresenta o aplicativo, suas funcionalidades e informações sobre as versões disponibilizadas ao público.

**O código-fonte permanece privado nesta fase, por questões de segurança.** Há a intenção de tornar o projeto **open source** no futuro, após a preparação para a abertura do código. Ainda não há uma data definida para essa publicação.

Por enquanto, este espaço é destinado à documentação pública, à divulgação das novidades e, quando disponíveis, aos instaladores do aplicativo.

## Funcionalidades

### Conta e perfil

- Cadastro e login com e-mail e senha.
- Confirmação de e-mail quando exigida no cadastro.
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
- Armazenamento privado dos comprovantes, com acesso associado à conta do usuário.

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
- Histórico de conversas, com recuperação das últimas 100 mensagens ao abrir o chat.
- Respostas geradas com inteligência artificial do Google Gemini.
- Tratamento de indisponibilidade temporária do serviço de IA.
- Acesso a partir dos atalhos de diagnóstico, códigos de falha e análise das leituras OBD2.

### Atualizações sem loja

- Versão instalada disponível na área de perfil.
- Botão **Buscar atualização** para consultar novas versões disponibilizadas pelo desenvolvedor.
- Comparação pelo número de compilação do aplicativo.
- Exibição da versão disponível e das notas da atualização.
- Abertura do link do APK no navegador, seguida da instalação confirmada pelo usuário no Android.

As versões para download, quando disponibilizadas, serão anunciadas na área **Releases** deste repositório.

## Download e instalação

Quando houver uma versão disponível, procure o APK na área **Releases** deste repositório.

1. Baixe o APK da versão desejada.
2. Abra o arquivo no aparelho Android.
3. Se solicitado, autorize a instalação pela fonte utilizada para abrir o APK.
4. Confirme a instalação e abra a AUTOGUARDIA.
5. Crie sua conta ou faça login para acessar seus veículos e registros.

O aplicativo ainda está em fase beta. A disponibilidade de instaladores e de novas versões será informada neste repositório.

### Como atualizar

No aplicativo, abra **Meu perfil → Buscar atualização**. Quando houver uma versão mais recente, consulte as novidades e toque em **Baixar atualização**. Depois do download, abra o APK e confirme a instalação no Android.

## O que é necessário para usar

- Aparelho Android compatível com a versão disponibilizada.
- Conta no aplicativo para acessar a garagem, os registros e o assistente.
- Conexão com a internet para acessar os dados da conta e utilizar a IA.
- Adaptador OBD2 compatível com ELM327 por Bluetooth clássico para obter leituras reais do veículo.
- Permissões de Bluetooth e, quando solicitada pelo Android, localização para a conexão com o adaptador.

As calculadoras fazem os cálculos no próprio aparelho. O modo de demonstração OBD2 permite conhecer o painel sem conectar um veículo.

## Dados e privacidade

- Os registros de veículos, manutenções, abastecimentos e conversas ficam associados à conta do usuário.
- Os comprovantes de manutenção possuem controle de acesso por proprietário.
- As preferências do painel OBD2 são salvas localmente no aparelho.
- O histórico gráfico dos sensores é mantido durante a sessão, em uma janela de 30 segundos; não é um registro permanente das viagens.
- Ao utilizar o assistente, mensagens e informações do veículo selecionado, incluindo manutenções recentes, podem ser enviadas ao provedor de IA para contextualizar a resposta.

## Relatar problemas e sugerir melhorias

Utilize a área **Issues** deste repositório para relatar bugs ou sugerir funcionalidades.

Ao relatar um problema, informe:

- Versão do aplicativo, disponível no perfil.
- Modelo do aparelho e versão do Android.
- Tela afetada e passos para reproduzir o problema.
- Comportamento esperado e o que aconteceu.
- Modelo do adaptador e veículo utilizado, se o problema envolver OBD2.

Evite incluir dados pessoais, documentos ou informações de acesso nos relatos públicos.

## Disponibilidade e limites

O foco atual é Android. O diagnóstico OBD2 depende da compatibilidade do veículo, do adaptador e dos parâmetros disponibilizados pela central eletrônica.

Os dados de consumo, autonomia, gastos e próximas revisões são estimativas baseadas nas informações registradas. O assistente depende da disponibilidade do serviço de IA.

As funções OBD2 e de IA ajudam a acompanhar informações e investigar sintomas. Uma leitura ou um código isolado não confirma a causa de uma falha; apagar códigos não corrige o problema mecânico.

## Futuro open source

A abertura do código faz parte dos planos do projeto. Quando essa etapa estiver pronta, as informações de acesso ao código, instalação para desenvolvimento e contribuição serão publicadas aqui.
