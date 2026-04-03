# Simulador MIC-1

Aplicação desktop interativa com interface gráfica em JavaFX que simula o funcionamento de um processador MIC-1, arquitetura descrita por Andrew S. Tanenbaum em _Structured Computer Organization_. O simulador oferece visualização completa dos componentes internos da CPU, incluindo registradores, memória, ULA, e memória de controle com suporte a microprogramação.

[![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![JavaFX](https://img.shields.io/badge/JavaFX-4B8BBE?style=flat-square&logo=java&logoColor=white)](https://gluonhq.com/products/javafx/)
[![Maven](https://img.shields.io/badge/Maven-C71A36?style=flat-square&logo=apache-maven&logoColor=white)](https://maven.apache.org/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)](https://www.docker.com/)
[![Tanenbaum](https://img.shields.io/badge/Tanenbaum-MIC1-blue?style=flat-square)](https://pt.wikipedia.org/wiki/Andrew_Stuart_Tanenbaum)

## Funcionalidades

- 🎯 **Simulação Completa do MIC-1** — Emula fielmente o processador MIC-1 conforme descrito por Tanenbaum
- 📊 **Visualização em Tempo Real** — Monitore registradores, memória e estado da CPU durante a execução
- ⚙️ **Microprogramação** — Carregue e execute programas em microinstruções com memória de controle
- 🧮 **ULA Completa** — Operações aritméticas e lógicas com flags de status (N e Z)
- 💾 **Gerenciamento de Memória** — Acesso completo à memória RAM com visualização hexadecimal
- 🎮 **Controle de Execução** — Passo a passo, execução contínua e controle de clock
- 📝 **Suporte a Múltiplos Formatos** — Carregamento de instruções e dados de arquivos CSV e TXT
- 🌐 **Interface Intuitiva** — Design responsivo com elementos visuais para fácil compreensão
- 🐳 **Docker Support** — Imagem Docker disponível para execução containerizada

---

## Pré-requisitos

- **JDK 11+** (compatível com Java 21). Verifique com `java -version`
- **Maven 3.6+** para build e gerenciamento de dependências. Verifique com `mvn -version`
- **Sistema Operacional**: Windows, macOS ou Linux
- (Opcional) **Docker** para execução em container

Para Ubuntu/Debian, instale com:

```bash
sudo apt-get install openjdk-21-jdk maven
```

Para macOS com Homebrew:

```bash
brew install openjdk maven
```

---

## Estrutura do Projeto

```
Simulador-MIC-1/
├── ProjectJavaFXML/
│   ├── src/main/java/mic/projectjavafxml/
│   │   ├── backend/                       # Lógica de simulação
│   │   │   ├── ALU.java                   # Unidade Lógica e Aritmética
│   │   │   ├── CPU.java                   # Processador MIC-1
│   │   │   ├── Memory.java                # Gerenciador de memória RAM
│   │   │   ├── MemoryLine.java            # Representação de linha de memória
│   │   │   ├── Register.java              # Registradores
│   │   │   ├── Shifter.java               # Deslocador de bits
│   │   │   ├── Mux.java                   # Multiplexadores
│   │   │   ├── MSeqLogic.java             # Lógica de sequenciamento
│   │   │   ├── CodeParser.java            # Parser de instruções
│   │   │   ├── InstructionParser.java     # Parser de microprogramação
│   │   │   ├── FileParser.java            # Parser de arquivos
│   │   │   ├── NumericFactory.java        # Conversão numérica
│   │   │   ├── ObservableResourceFactory.java  # Factory de recursos
│   │   │   └── CodeParserException.java   # Exceções
│   │   └── sample/                        # Camada de apresentação
│   │       ├── Main.java                  # Ponto de entrada
│   │       └── Controller.java            # Controlador de UI
│   ├── src/main/resources/
│   │   ├── fxml/
│   │   │   └── main.fxml                  # Interface em FXML
│   │   ├── css/
│   │   │   └── styles.css                 # Estilos da aplicação
│   │   ├── dataFiles/
│   │   │   ├── controlMemory.txt          # Memória de controle padrão
│   │   │   ├── controlMemoryINT.txt       # Memória com interrupções
│   │   │   ├── microprogram.txt           # Exemplo de microprograma
│   │   │   └── supportedInstructions.csv  # Instruções suportadas
│   │   ├── img/datapath/                  # Imagens da arquitetura
│   │   └── Translation_en_US.properties   # Internacionalização
│   ├── pom.xml                            # Configuração Maven
│   └── nbactions.xml                      # Ações NetBeans
└── README.md                              # Este arquivo
```

### Dependências Principais

```xml
<!-- JavaFX - Interface Gráfica -->
<dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-controls</artifactId>
    <version>13</version>
</dependency>
<dependency>
    <groupId>org.openjfx</groupId>
    <artifactId>javafx-fxml</artifactId>
    <version>13</version>
</dependency>
```

---

## Primeira Inicialização (Passo a Passo)

### 1. Verifique a Instalação do Java e Maven

```bash
java -version
mvn -version
```

Ambos devem exibir versões compatíveis.

### 2. Clone ou Baixe o Repositório

```bash
git clone https://github.com/Gurkan22/Simulador-MIC-1.git
cd Simulador-MIC-1/ProjectJavaFXML
```

### 3. Baixe as Dependências com Maven

```bash
mvn clean install
```

Isso compilará o projeto e preparará tudo para execução.

### 4. Execute a Aplicação

```bash
mvn javafx:run
```

Ou, se preferir:

```bash
mvn exec:java@run
```

A janela do simulador MIC-1 abrirá com resolução padrão de 1280x720.

### 5. (Opcional) Carregue Microprogramas

Ao iniciar, você pode carregar arquivos de controle e microprogramas localizados em `src/main/resources/dataFiles/`:

- `controlMemory.txt` — Microinstruções padrão
- `controlMemoryINT.txt` — Microinstruções com suporte a interrupções
- `microprogram.txt` — Exemplo de programa para execução

---

## Build & Geração de Executáveis

### JAR Executável

```bash
mvn clean package
```

O JAR gerado estará em:

```
target/ProjectJavaFXML-1.0.jar
```

Para executar:

```bash
java -jar target/ProjectJavaFXML-1.0.jar
```

### Modo Debug

```bash
mvn -X javafx:run
```

Para análise de problemas e rastreamento detalhado.

### Build com Maven Assembly Plugin (opcional)

Se configurado, cria um JAR com todas as dependências embutidas:

```bash
mvn clean assembly:assembly
```

---

## Docker

### Build da Imagem

```bash
docker build -t mic-sim:latest .
```

### Executar Container

```bash
docker run -it --rm \
  -e DISPLAY=$DISPLAY \
  -v /tmp/.X11-unix:/tmp/.X11-unix \
  mic-sim:latest
```

**Nota**: A execução com interface gráfica via Docker requer X11 forwarding configurado no sistema host.

### Usar Imagem do DockerHub

```bash
docker pull reksee/mic-sim-app
docker run -it --rm reksee/mic-sim-app
```

---

## Uso da Aplicação

### Interface Principal

1. **Painel de Registradores** — Visualiza o estado de PC, SP, AC, etc.
2. **Visor de Memória** — Exibe conteúdo da RAM em hexadecimal
3. **Controles de Execução** — Botões para step, run e reset
4. **Memória de Controle** — Carregamento e visualização de microinstruções
5. **Visualização da Arquitetura** — Diagrama com componentes do MIC-1

### Fluxo Típico

1. Inicie o simulador
2. Carregue um arquivo de controle (`controlMemory.txt`)
3. Carregue um microprograma (`microprogram.txt`)
4. Execute passo a passo ou em modo contínuo
5. Monitore o estado dos registradores e memória em tempo real

---

## Componentes Principais

### CPU.java

Simula o processador MIC-1 com todos os registradores, multiplexadores e lógica de sequenciamento.

### ALU.java

Implementa operações aritméticas e lógicas com flags N (negativo) e Z (zero).

### Memory.java

Gerencia 64KB de memória RAM com acesso via MAR (Memory Address Register).

### MSeqLogic.java

Lógica de sequenciamento de microinstruções baseada em sinais de controle.

### CodeParser.java

Analisa e valida código de instrução carregado de arquivos.

### Shifter.java

Implementa operações de deslocamento de bits necessárias no MIC-1.

---

## Problemas Comuns e Soluções

| Problema                             | Solução                                                                |
| ------------------------------------ | ---------------------------------------------------------------------- |
| `Module not found: javafx.controls`  | Execute `mvn clean install` para baixar dependências                   |
| Aplicação não inicia                 | Verifique Java 11+ com `java -version`                                 |
| Erro de compilação `--module-path`   | Certifique-se de que Maven e Maven plugin de JavaFX estão configurados |
| Interface não aparece                | Tente `mvn javafx:run -X` para debug                                   |
| Erro ao carregar arquivo de controle | Verifique formato CSV/TXT em `src/main/resources/dataFiles/`           |
| Memória não atualiza                 | Reinicie a aplicação e recarregue o programa                           |

---

## Desenvolvimento

### Compilar e Testar

```bash
mvn clean compile
```

### Análise de Código

```bash
mvn pmd:pmd
```

### Gerar Documentação JavaDoc

```bash
mvn javadoc:javadoc
```

Acesse em: `target/site/apidocs/index.html`

### Hot Reload (Desenvolvimento)

Para alterações rápidas durante desenvolvimento:

```bash
mvn javafx:run
```

Pressione Ctrl+C para parar e reexecute para recarregar mudanças.

---

## Arquitetura MIC-1

O MIC-1 é um processador RISC educacional com:

- **16 registradores** de 16 bits (PC, SP, AC, etc.)
- **32KB de memória principal** endereçada por 16 bits
- **4 níveis de pipeline** (IF, OF, EX, WB)
- **ULA de 16 bits** com suporte a múltiplas operações
- **Memória de controle ROM** com microinstruções
- **Lógica de sequenciamento** para microprogramação

Referência: _Structured Computer Organization_ — Andrew S. Tanenbaum, 6ª edição.

---

## Notas para Produção

- Sempre compile em Release com `mvn clean package`
- Teste em múltiplas plataformas (Windows, macOS, Linux) antes de distribuir
- Para distribuição, considere usar o Java Runtime Environment (JRE) mínimo necessário
- Implemente validação adicional de entrada para microprogramas
- Considere adicionar suporte a breakpoints e watchpoints para debug avançado
- Mantenha backups dos arquivos de controle (`dataFiles/`)

---

## Referências Acadêmicas

- [Structured Computer Organization - Andrew S. Tanenbaum](https://www.pearson.com/en-us/subject-catalog/p/structured-computer-organization/P200000003513)
- [JavaFX Documentation](https://gluonhq.com/products/javafx/)
- [Maven Documentation](https://maven.apache.org/guides/)
- [MIC-1 Architecture Overview](https://en.wikipedia.org/wiki/Microarchitecture)

---

## Autores

Desenvolvido por graduandos em **Ciência da Computação** da **Universidade Federal Fluminense (UFF)**, Brasil, Rio de Janeiro.

Projeto educacional voltado ao ensino de arquitetura de computadores e microprogramação.

Brenda Lopes da Silva
Pedro Albuquerque Braga dos Santos
Pedro Lucas Almeida dos Santos
Ramon Fernando Antunes da Silva
---
