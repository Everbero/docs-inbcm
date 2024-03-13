# Tieta - Tainacan INBCM Exporter Tool App

Este plugin adicionar um exportador de dados para o fortamo XLSX. 

## Objetivos

1. Implementar um novo tipo de exportador no menu "Exportadores" do plugin Tainacan.
2. Permitir que o usuário selecione uma coleção para exportar e escolha sua especificidade: Museologia, Biblioteconomia ou Arquivologia.
3. Gerar uma planilha de acordo com o modelo fornecido, após o usuário clicar em "Executar".
4. Disponibilizar o arquivo da planilha para download imediato após sua geração.
5. Assegurar compatibilidade com as versões mais recentes do WordPress e do plugin Tainacan.  


## Funcionamento

**Adição de opção de exportador:**  
Este plugin estende a classe ```\Tainacan\Exporter``` e adiciona uma nova opção de exportação de dados. 
Para mais informações sobre este processo visite a [Documentação](https://tainacan.github.io/tainacan-wiki/#/dev/exporter-flow)

**Geração de tipos de arquivos XLXS:**  
Este plugin extenderá a classe ``` Tainacan\Exposers\Mappers``` para gerar aquivos de dados nos padrões especificados pela [Resolução Normativa IBRAM nº 6, de 31 de agosto de 2021.](https://www.gov.br/museus/pt-br/assuntos/legislacao-e-normas/outros-instrumentos-normativo/resolucao-normativa-ibram-no-6-de-31-de-agosto-de-2021#:~:text=Decreto%20n%C2%BA%208.124%2C%20de%2017,20%20de%20janeiro%20de%202009.)
Para mais informações sobre este processo visite a [Documentação](https://tainacan.github.io/tainacan-wiki/#/dev/mapping-standards?id=examples)