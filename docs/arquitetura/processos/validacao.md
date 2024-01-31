# Processo de Validação e Retificação de Dados do Inventário Musealizado

Para garantir a integridade e consistência dos dados do inventário musealizado, o sistema implementará um processo robusto de validação e retificação. Ao receber uma declaração, o sistema realizará as seguintes verificações:

## Validação do Arquivo CSV:

1. **Existência e Preenchimento:** O sistema verificará a presença do arquivo CSV e se todos os campos obrigatórios estão devidamente preenchidos. Caso contrário, a declaração será marcada como inválida.

## Validação dos Arquivos de Imagem:

1. **Existência:** Para cada item do inventário que possui imagens associadas, o sistema verificará a existência dos arquivos de imagem conforme especificado no CSV. Itens sem imagens serão considerados válidos.

## Associação com o Museu de Origem:

Cada arquivo enviado será associado ao museu de origem, garantindo a rastreabilidade dos dados. Essa associação permitirá a validação do museu no momento do envio das informações, através do login e senha na plataforma Museus.Br.

## Identificação Temporal e Checksum:

1. **Identificação Temporal:** Cada envio será marcado com uma identificação temporal dentro do período de recebimento. Isso permitirá rastrear e comparar diferentes declarações no tempo.

2. **Checksum do Pacote de Dados:** Será calculado um checksum para o pacote de dados (CSV e imagens), garantindo a integridade do conjunto. Esse checksum será utilizado para verificar a consistência dos dados durante o processo de retificação.

## Processo de Retificação:

Em caso de necessidade de retificação, o usuário poderá realizar as correções necessárias no inventário e reenviar os dados. O sistema identificará a declaração anterior, comparará os checksums e garantirá que apenas as retificações necessárias sejam aplicadas.