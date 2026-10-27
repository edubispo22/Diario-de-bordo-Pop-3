# POP 100 — Diário de Bordo (APK pelo GitHub)

Este projeto empacota o HTML fornecido em um aplicativo Android usando Capacitor e gera um APK de teste pelo GitHub Actions.

## O que está incluído
- `www/index.html`: aplicativo HTML original enviado pelo usuário.
- `package.json`: dependências do Capacitor.
- `capacitor.config.json`: nome e identificador do app.
- `.github/workflows/build-apk.yml`: compilação automática do APK.

## Como gerar o APK usando o GitHub

1. Entre em https://github.com e crie um repositório novo, por exemplo `pop100-diario-de-bordo`.
2. Envie todos os arquivos e pastas deste ZIP para a raiz do repositório. Não envie apenas o arquivo HTML.
3. Aguarde a execução automática: no repositório, abra a aba **Actions** e clique no fluxo **Gerar APK Android**.
4. Quando a execução terminar com um visto verde, abra a execução e procure **Artifacts**.
5. Baixe `POP100-Diario-de-Bordo-APK` e extraia o ZIP baixado.
6. Copie `app-debug.apk` para o celular Android e abra-o para instalar. Talvez seja necessário autorizar a instalação dessa fonte nas configurações do Android.

Se o fluxo não iniciar automaticamente, abra **Actions**, selecione **Gerar APK Android** e clique em **Run workflow**.

## Observações importantes
- Este é um APK de depuração para instalação e teste, não um APK de lançamento assinado para publicação na Play Store.
- O HTML original usa `localStorage` para guardar dados no dispositivo. Os dados ficam no armazenamento local do aplicativo; desinstalar o app pode apagá-los. Use regularmente a função **Backup (JSON)** dentro do aplicativo e guarde o arquivo em outro lugar.
- O aplicativo original começa com dados de demonstração. Ao abrir, use **Limpar e começar** antes de inserir seus dados reais.
- Exportação CSV/relatórios no HTML original tentam usar `claude.use("downloads")`, recurso específico do ambiente Claude. Fora dele, pode aparecer uma caixa com o conteúdo para copiar manualmente. O backup JSON e restauração também devem ser testados no Android.
- O workflow cria a pasta `android/` durante a compilação; ela não precisa estar no repositório.
- Para gerar novas versões, envie as alterações ao GitHub. Cada envio para `main` ou `master` inicia uma nova compilação.

## Estrutura
```text
.
├── .github/
│   └── workflows/
│       └── build-apk.yml
├── www/
│   └── index.html
├── capacitor.config.json
├── package.json
├── .gitignore
└── README.md
```
