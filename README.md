# Fuzuê Bar & Club - Landing Page Oficial

![[Logo Principal Fuzuê Bar]](https://firebasestorage.googleapis.com/v0/b/fuzuetest.firebasestorage.app/o/Untitled_design-removebg-preview.png?alt=media)

Bem-vindo ao repositório oficial da landing page do Fuzuê Bar & Club! Esta página foi desenvolvida para apresentar o bar, suas atrações, agenda de eventos, sistema de reservas e informações de contato, com o objetivo de ser lançada para web para o funcionamento do bar.

## Sobre o Fuzuê Bar & Club

O Fuzuê é mais que um bar, é uma experiência completa! Localizado em Fortaleza, CE, oferecemos ambientes aconchegantes, comidinhas deliciosas, drinks caprichados e uma programação musical vibrante com DJs residentes e convidados. Seja para um happy hour, uma celebração especial ou apenas para curtir a noite, o Fuzuê é o seu ponto de encontro.

**Unidades:**
* **Fuzuê Bar:** Rua Barão de Aracati, 609 - Meireles, Fortaleza - CE
* **Fuzuê Club:** R. José Avelino, 349 - Centro, Fortaleza - CE

## ✨ Funcionalidades da Landing Page

* **Design Atraente e Responsivo:** Interface moderna e adaptável a diferentes dispositivos (desktop, tablets e mobile).
* **Navegação Intuitiva:** Menu fixo para fácil acesso às seções:
    * **Sobre Nós:** Apresentação do bar e galeria de fotos.
    * **Cardápio:** Link para o cardápio completo em PDF.
    * **Agenda:** Programação de eventos e atrações.
    * **Lineup de DJs:** Apresentação dos DJs residentes com prévias musicais e links para redes sociais.
    * **Reservas:** Sistema de reserva de mesas para diferentes áreas do bar e para entrada no Fuzuê Club.
    * **Localização:** Mapas interativos para as duas unidades (Bar e Club).
    * **Contato:** Links diretos para redes sociais (Instagram) e WhatsApp.
    * **Dúvidas Frequentes (FAQ):** Respostas para as perguntas mais comuns.
* **Galerias Interativas:**
    * Carrossel de fotos do ambiente com lightbox para visualização ampliada.
    * Carrossel de DJs com prévias de áudio.
* **Sistema de Reservas Integrado:**
    * Formulário modal para coleta de dados do cliente (Nome, CPF, Telefone, Área/Tipo de Reserva, Quantidade de Pessoas, Data).
    * As reservas são salvas no **Firebase Firestore**.
    * As reservas também são enviadas para uma **Planilha Google Sheets** para gerenciamento pela equipe de recepção.
    * Notificação de nova reserva para o administrador via link do WhatsApp.
* **Animações Suaves:** Efeitos de transição e aparição de elementos durante a rolagem da página.
* **Wallpapers Dinâmicos:** Fundos personalizados para cada seção, carregados do Firebase Storage.

## 🚀 Tecnologias Utilizadas

* **HTML5:** Estrutura da página.
* **CSS3:** Estilização e design visual.
* **Tailwind CSS:** Framework CSS para desenvolvimento rápido e responsivo.
* **JavaScript (ES6+ Modules):** Interatividade, manipulação do DOM, lógica de animações e integrações.
* **Firebase:**
    * **Firestore:** Banco de dados NoSQL para armazenamento das reservas.
    * **Firebase Storage:** Armazenamento de imagens (logos, wallpapers, fotos da galeria, etc.) e do arquivo PDF do cardápio.
    * **Firebase Authentication:** Autenticação anônima para identificação de usuários no Firestore (pode ser expandida).
* **Google Apps Script:** Para integração do sistema de reservas com o Google Sheets.
* **Font Awesome:** Biblioteca de ícones.
* **Google Fonts:** Para tipografia personalizada.

## ⚙️ Configuração e Instalação Local

Para rodar este projeto localmente, siga os passos abaixo:

1.  **Clone o Repositório:**
    ```bash
    git clone [https://github.com/SEU_USUARIO_GITHUB/NOME_DO_SEU_REPOSITORIO.git](https://github.com/SEU_USUARIO_GITHUB/NOME_DO_SEU_REPOSITORIO.git)
    cd NOME_DO_SEU_REPOSITORIO
    ```

2.  **Crie o Arquivo de Configuração (`config.js`):**
    Na raiz do projeto (mesma pasta do `index.html`), crie um arquivo chamado `config.js`. Este arquivo **não deve ser versionado** no Git (adicione-o ao seu `.gitignore`).
    Copie o seguinte conteúdo para o seu `config.js` e **substitua os placeholders pelos seus valores reais**:

    ```javascript
    // config.js
    // ATENÇÃO: Adicione este arquivo ao seu .gitignore para não expor suas chaves!

    // Configuração do Firebase (para ambiente local ou fallback)
    const firebaseConfigSettings = {
        apiKey: "SUA_API_KEY_AQUI",
        authDomain: "SEU_AUTH_DOMAIN_AQUI.firebaseapp.com",
        projectId: "SEU_PROJECT_ID_AQUI",
        storageBucket: "SEU_STORAGE_BUCKET_AQUI.appspot.com", // ou .firebasestorage.app
        messagingSenderId: "SEU_MESSAGING_SENDER_ID_AQUI",
        appId: "SEU_APP_ID_AQUI",
        measurementId: "SEU_MEASUREMENT_ID_AQUI" // Opcional, mas recomendado
    };

    // URL do seu Google Apps Script para integração com a planilha
    // Substitua pelo URL real do seu script implantado.
    const googleAppsScriptUrlSettings = 'SEU_URL_DO_APPS_SCRIPT_AQUI';

    // App ID padrão para o Firebase (usado nos paths do Firestore, por exemplo)
    const defaultAppIdSettings = 'default-fuzuebar-app-local'; // Pode ser qualquer string para ambiente local

    // Número do WhatsApp do Administrador para notificações de reserva
    const adminWhatsAppNumberSettings = "55SEUWHATSAPPNUMBER"; // Ex: 5585999998888

    // Disponibiliza as configurações globalmente para o script principal
    window.firebaseConfigFallback = firebaseConfigSettings;
    window.GOOGLE_APPS_SCRIPT_URL_CONFIG = googleAppsScriptUrlSettings;
    window.DEFAULT_APP_ID_CONFIG = defaultAppIdSettings;
    window.ADMIN_WHATSAPP_NUMBER_CONFIG = adminWhatsAppNumberSettings;
    ```

3.  **Configure o Firebase:**
    * Crie um projeto no [Firebase Console](https://console.firebase.google.com/).
    * Adicione um aplicativo da Web ao seu projeto.
    * Copie as credenciais de configuração do Firebase (apiKey, authDomain, etc.) e cole-as no seu `config.js`.
    * Ative o **Firestore** no modo de produção ou teste.
    * Configure o **Firebase Storage** e faça o upload dos seus assets (imagens, PDF do cardápio) para as pastas correspondentes. Certifique-se de que os nomes dos arquivos e caminhos no Storage correspondem aos definidos no `index.html` (nas constantes de URL).
    * Ajuste as **Regras de Segurança** do Firestore para permitir escrita na coleção de reservas (ex: `artifacts/{appId}/public/data/reservas_fuzuebar`).
    * Ajuste as **Regras de Segurança** do Storage para permitir leitura pública dos seus assets:
        ```
        rules_version = '2';
        service firebase.storage {
          match /b/{bucket}/o {
            match /{allPaths=**} {
              allow read: if true;
              // allow write: if request.auth != null; // Se necessário
            }
          }
        }
        ```

4.  **Configure a Integração com Google Sheets (Opcional, mas recomendado para reservas):**
    * Crie uma nova Planilha Google.
    * Abra a planilha e vá em **Extensões > Apps Script**.
    * Copie o código do Apps Script fornecido nos comentários do arquivo `index.html` (procure por `/* Apps Script Example... */`) e cole no editor do Apps Script da sua planilha. **Certifique-se de atualizar o `sheetUrl` dentro do Apps Script para o URL da sua própria planilha.**
    * Clique em **Implantar > Nova implantação**.
        * Tipo: **Aplicativo da Web**.
        * Descrição: (ex: "Receptor de Reservas Fuzuê").
        * Executar como: **Eu (seuemail@gmail.com)**.
        * Quem pode acessar: **Qualquer pessoa**.
    * Clique em "Implantar" e autorize o script.
    * Copie o **URL do aplicativo da Web** fornecido e cole-o na variável `googleAppsScriptUrlSettings` no seu `config.js`.

5.  **Abra com um Servidor Local:**
    * Use uma extensão como o "Live Server" no VS Code ou qualquer outro servidor HTTP local para servir o `index.html`. Isso é importante para que as requisições de módulo (`type="module"`) e fetches funcionem corretamente.

## 🖼️ Estrutura de Assets (Exemplo no Firebase Storage)

Para que as imagens e o cardápio carreguem corretamente, espera-se a seguinte estrutura de arquivos no seu bucket do Firebase Storage (ex: `gs://fuzuetest.firebasestorage.app/`):

* `Untitled_design-removebg-preview.png` (Logo principal)
* `LOGOS_FUZUE-03.png` (Logo do Garden)
* `Cardapio.pdf`
* `canva_fuz (2).png` (Wallpaper global/hero)
* `footer - fuzue.png` (Imagem de fundo do rodapé)
* `baby devil fuz.jpg` (Galeria - Foto 1)
* `comida fuz.jpg` (Galeria - Foto 2)
* `promo quarta fuz.jpg` (Galeria - Foto 3)
* `foto_everon.jpg` (Foto DJ Everon)
* `defarias.jpg` (Foto DJ DeFarias)
* `rafiusk.jpg` (Foto DJ Rafiusk)
* `dj lineup.png` (Wallpaper da seção Lineup)
* `reserva_mesa.png` (Wallpaper da seção Reservas)
* `localização.png` (Wallpaper da seção Localização)
* `contato_background.png` (Wallpaper da seção Contato)
* `duvidas_freqs.png` (Wallpaper da seção FAQ)
* `agenda_wallpaper.png` (Wallpaper da seção Agenda)

## 🎨 Customização

* **Fontes:** A fonte principal 'Engebrechtre' precisa ser carregada. Se for uma fonte customizada, adicione-a via `@font-face` no CSS ou use um link CDN.
* **Cores e Estilos:** As cores principais e estilos estão definidos no bloco `<style>` dentro do `index.html`. Você pode ajustá-los conforme a identidade visual do Fuzuê.
* **Wallpapers:** Os wallpapers de cada seção são carregados dinamicamente via JavaScript. Para alterar uma imagem, basta atualizar o nome do arquivo correspondente no Firebase Storage e, se necessário, a constante no script.
* **Conteúdo Textual:** Todo o conteúdo textual (descrições, informações de eventos, FAQ) pode ser editado diretamente no HTML.

## 🤝 Contribuições

Contribuições são bem-vindas! Se você encontrar algum bug ou tiver sugestões de melhorias, sinta-se à vontade para abrir uma *Issue* ou enviar um *Pull Request*.

## 📜 Licença

Este projeto é para uso exclusivo do Fuzuê Bar & Club. Por favor, entre em contato antes de reutilizar o código para outros fins.

---

*Desenvolvido com ❤️ para o Fuzuê!*
