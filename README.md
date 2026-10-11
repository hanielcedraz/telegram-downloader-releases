# Telegram Downloader

Aplicativo de desktop (Windows e macOS) para **encontrar, analisar e baixar
arquivos de grupos e canais do Telegram de forma organizada** — pensado para
quem junta modelos 3D (`.stl`, `.3mf`, `.obj`, `.step`, `.gcode`...), mas que
funciona com qualquer tipo de arquivo.

Este repositório publica **só os programas prontos** (aba
[Releases](../../releases/latest)). Não é preciso instalar Python nem nenhuma
biblioteca: baixe, abra e use.

> O código-fonte é mantido em um repositório privado.

---

## Baixar

**➡ [Última versão](../../releases/latest)**

| Sistema | Arquivo | Requisitos |
|---|---|---|
| Windows | `TelegramDownloader-vX.Y.Z-windows.exe` | Windows 10 ou 11, 64 bits |
| macOS | `TelegramDownloader-vX.Y.Z-macos.zip` | Mac com chip Apple (M1 ou mais novo)* |

A versão (`vX.Y.Z`) vai no nome do arquivo. Versões antigas continuam
disponíveis na aba Releases.

\* O app macOS é compilado em máquina Apple Silicon. Em Macs com processador
Intel ele pode não abrir.

### Windows

1. Baixe o `.exe` e salve em **Downloads** ou no **Desktop** (não execute
   direto do navegador).
2. Dê duplo clique. É um único arquivo, sem instalador.
3. Opcional: abra o app e clique em **Atalho no Iniciar** (topo da janela).
   Ele guarda o `.exe` numa pasta fixa e cria o atalho no Menu Iniciar (e, se
   quiser, na Área de Trabalho). Depois pode apagar o arquivo baixado.

O programa ainda **não é assinado digitalmente**, então o Windows pode barrar
na primeira vez:

- **SmartScreen** ("O Windows protegeu o computador"): clique em
  **Mais informações → Executar assim mesmo**.
- **Smart App Control** ("blocked an app that may be unsafe"): esse não tem
  botão para liberar. Veja [Problemas comuns](#problemas-comuns).

### macOS

1. Baixe o `.zip` e dê duplo clique para descompactar.
2. Arraste **Telegram Downloader.app** para a pasta **Aplicativos**.
3. Na primeira vez, clique com o botão **direito** no app → **Abrir**
   (o macOS avisa que é de um desenvolvedor não identificado).

---

## Primeiro uso

O app usa a sua própria conta do Telegram e pede duas credenciais gratuitas,
**api_id** e **api_hash**. A tela de configuração tem um botão que leva direto
à página onde obtê-las:

1. Acesse `my.telegram.org` e entre com seu telefone (o código chega no app do
   Telegram).
2. Abra **API development tools** e crie um aplicativo (título e nome curto
   podem ser qualquer coisa; plataforma **Desktop**).
3. Copie *App api_id* e *App api_hash* para o programa.
4. Informe seu telefone e o código de login. A sessão fica salva — isso só
   acontece uma vez.

> ⚠ Essas credenciais são pessoais e dão acesso à sua conta. Não compartilhe.
>
> ⚠ Ao receber o código de login, **não abra a conversa** do Telegram onde ele
> chegou: o Telegram invalida códigos lidos dentro do app. Copie pela
> notificação ou peça outro código.

---

## O que o programa faz

- **Análise sem baixar nada** — lê só os metadados do histórico e mostra
  quantos arquivos e quantos GB existem, por categoria e tipo.
- **Uma aba por grupo** — analise vários grupos ao mesmo tempo e compare.
- **Cache** — a segunda análise de um grupo busca só as mensagens novas.
- **Pré-visualização** — mostra a foto do mesmo post antes de você baixar.
- **Visão por modelo** — junta versões e partes do mesmo modelo
  (`suporte_v2.stl`, `suporte_final.3mf`, a foto do post) num só item e marca
  duplicatas.
- **Download organizado** — escolhe categorias, tipos ou arquivos avulsos e
  baixa em pastas organizadas, com barra de progresso e cancelamento.
- **Buscar em todos os grupos** — procura um nome (aceita erro de digitação,
  plural e acento) em todos os seus grupos, analisando os que ainda não foram
  analisados. Opcionalmente procura também em grupos públicos fora da sua lista.
- **Descobrir grupos** — acha grupos e canais públicos sobre um assunto; os
  que você analisar ficam na aba Grupos como «não membro».
- **Filtro de extensões** — depois de analisar, lista as extensões que existem
  no grupo e mostra só as que você marcar.
- **Sem links de promoção** — posts que são só link e `@canais` nas legendas
  ficam fora das análises e da busca.
- **Encaminhar** — manda arquivos selecionados para outro chat.
- **Atualização automática** — botão *Verificar atualizações* (veja abaixo).

---

## Atualizações

No topo do app, o botão **Verificar atualizações** consulta esta página de
releases. Se houver versão nova, **Baixar e instalar** baixa o arquivo certo
para o seu sistema, fecha o app e reabre já atualizado. O app também confere
sozinho, em segundo plano, ao abrir.

Se preferir, baixe a versão nova aqui na aba Releases e substitua o arquivo
antigo.

---

## Privacidade e segurança

- Tudo roda **no seu computador**. O programa só se conecta ao **Telegram** (com
  a sua conta) e ao **GitHub** (para checar atualizações).
- Credenciais, sessão e cache ficam na pasta `.tg_downloader`, dentro da sua
  pasta de usuário (Windows: `C:\Users\<você>\.tg_downloader`). Apagar essa
  pasta desconecta a conta e limpa o cache.
- O programa não envia seus dados nem arquivos para nenhum outro servidor.
- Use apenas em conteúdo que você tem direito de baixar, respeitando os termos
  do Telegram e os direitos de quem publicou os arquivos.

---

## Problemas comuns

**Windows: "Smart App Control blocked an app that may be unsafe"**
O Smart App Control bloqueia programas sem assinatura e não oferece "executar
assim mesmo". Salve o `.exe` em Downloads/Desktop e abra por lá. Se continuar
bloqueando, desligue o recurso em **Configurações → Privacidade e segurança →
Segurança do Windows → Controle de aplicativos e navegador → Smart App
Control** (depois de desligado, não dá para ligar de novo sem reinstalar o
Windows).

**Erro "Failed to load Python DLL ... python312.dll" depois de atualizar**
Feche o app e abra o `.exe` de novo com duplo clique — o arquivo já foi
trocado. Se não abrir, baixe a versão nova na aba Releases e substitua o
arquivo. (Corrigido a partir da v2.6.3: se você estiver numa versão anterior,
use o download manual uma vez.)

**"database is locked" ao conectar**
Há outra cópia do app aberta usando a mesma sessão. Feche todas as janelas; se
precisar, finalize `TelegramDownloader.exe` no Gerenciador de Tarefas e abra de
novo.

**macOS: "app de desenvolvedor não identificado"**
Botão direito no app → **Abrir** (só na primeira vez).

**O Telegram pediu para esperar (flood wait)**
Muitas requisições em pouco tempo. Aguarde o tempo indicado; o app mostra
resultados parciais quando isso acontece.

---

## Dúvidas e problemas

Abra uma **issue** neste repositório informando a versão do app, o sistema
(Windows/macOS) e, se possível, as últimas linhas da área de atividade (log) do
programa. Não inclua `api_id`, `api_hash`, telefone nem códigos de login.
