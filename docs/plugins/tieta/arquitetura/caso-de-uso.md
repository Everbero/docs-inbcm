### Caso de uso

Visando a simplicidade de uso do plugin os padrões de usabilidade seguem as especificações do Tainacan, inserindo uma nova opção de exportador no menu tainacan. As funcionalidades do plugin podem ser ilustradas de acordo com o diagrama abaixo:

```mermaid
graph TD
    A[Usuário] -->|Selecionar Coleção| B(Selecionar Coleção)
    A -->|Escolher Especificidade| C(Escolher Especificidade)
    A -->|Exportar para XLSX| D(Exportar para XLSX)
    A -->|Baixar Arquivo| E(Baixar Arquivo)
    
    C -->|Museologia| F(Museologia)
    C -->|Biblioteconomia| G(Biblioteconomia)
    C -->|Arquivologia| H(Arquivologia)
```