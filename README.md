# AutoTasy

Um repositório para centralizar as *releases* do projeto de automação **AutoTasy**.

---

## 🤖 AutoTasy

O **AutoTasy** é uma aplicação de automação desenvolvida em **Python**. Seu principal objetivo é simplificar e automatizar processos repetitivos no sistema Tasy, (comumente utilizado em ambientes hospitalares).

O script Python é compilado em um arquivo executável (`AutoTasy.exe`) que, ao ser iniciado, executa tarefas de automação, como o preenchimento automático de credenciais de login em painéis ou a abertura de módulos específicos.

---

## ⚠️ Requisito Obrigatório: Administrador

Para que os scripts `install.bat` ou `remove.bat` funcionem, eles **DEVE** ser executados com privilégios de Administrador.

1.  Baixe a última versão do AutoTasy.
2.  Clique com o **botão direito** no arquivo `.bat`.
3.  Selecione a opção **"Executar como administrador"**.

Se você apenas clicar duas vezes, o script falhará, pois não terá permissão para modificar as pastas de inicialização do sistema.

---

## ⚙️ `install.bat` (Instalação)

O script `install.bat` é usado para **adicionar** o atalho do AutoTasy na inicialização do Windows.

### Como Utilizar

O script de instalação (`install.bat`) e o atalho (`AutoTasy.lnk`) são distribuídos juntos nas *Releases*.

1.  Vá até a seção Releases e baixe o arquivo `.zip` da versão mais recente.
2.  Extraia o conteúdo (que deve incluir `install.bat` e `AutoTasy.lnk`) para uma pasta.
3.  Clique com o botão direito no `install.bat` e **Execute como administrador**.

### O que ele faz?

Ao ser executado, o script `install.bat` irá:
1.  Verificar se o arquivo `AutoTasy.lnk` está na mesma pasta que ele.
2.  Copiar o `AutoTasy.lnk` para a pasta de inicialização comum do Windows.

---

## 📍 Onde os Arquivos são Salvos (Destino)

Para que o atalho inicie para **todos os usuários** da máquina, o script o salva na pasta `shell:startup`.

O caminho completo desta pasta é:
`%ALLUSERSPROFILE%\Microsoft\Windows\Start Menu\Programs\StartUp`

Que, na maioria dos sistemas Windows, resolve para:
`C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp`

*(Nota: O executável `AutoTasy.exe` em si **não** é movido. O script move apenas o **atalho** `.lnk` que aponta para o executável. O `AutoTasy.exe` deve estar em um local fixo no computador, como `C:\Program Files\AutoTasy` ou similar.)*

---

## ❌ `remove.bat` (Remoção)

O script `remove.bat` é usado para **remover** com segurança o atalho `AutoTasy.lnk` da inicialização do Windows.

### Como Utilizar

1.  Baixe o `remove.bat` da última release.
2.  Clique com o botão direito no `remove.bat` e **Execute como administrador**.

### O que ele faz?

O script de remoção é mais robusto e segue vários passos para garantir a limpeza:

1.  **Verifica Permissões:** O script primeiro verifica se está sendo executado como Administrador.
2.  **Finaliza o Processo:** Ele tenta finalizar (matar) qualquer processo em execução chamado `AutoTasy.exe`. Isso é feito para "destravar" o atalho, caso ele esteja em uso.
3.  **Deleta o Atalho:** O script então procura e deleta o arquivo `AutoTasy.lnk` das pastas de inicialização (tanto da pasta "Comum / Todos os Usuários" quanto da pasta do "Usuário Atual", por segurança).
4.  **Confirmação:** O script exibirá uma mensagem informando se a operação foi bem-sucedida.
