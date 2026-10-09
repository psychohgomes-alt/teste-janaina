# Prospere Gestão Empresarial — site fullstack

Site institucional responsivo da Prospere, baseado no briefing recebido e na identidade visual anexada.

## Requisitos
- Node.js 20+
- Conta/servidor SMTP para habilitar o envio do formulário (não há armazenamento local de mensagens)

## Executar localmente
```bash
cp .env.example .env
npm install
npm run check
npm test
npm run dev
```
Acesse `http://localhost:3000`.

## Ativar formulário
Preencha no `.env`: `SMTP_HOST`, `SMTP_PORT`, `SMTP_SECURE`, `SMTP_USER`, `SMTP_PASS`, `SMTP_FROM` e `CONTACT_TO`. O servidor não registra o corpo das mensagens. Sem SMTP, o endpoint retorna indisponibilidade e a interface orienta o usuário a usar o e-mail comercial.

## Antes de publicar
1. Configurar HTTPS, domínio, SMTP e variáveis de ambiente no provedor.
2. Confirmar o número do WhatsApp e os links oficiais de Instagram/LinkedIn; os botões opcionais só aparecem quando configurados.
3. Obter autorização escrita antes de publicar nomes, marcas, depoimentos ou detalhes de projetos de clientes.
4. Revisar política de privacidade com os dados reais do controlador e do canal de atendimento.
5. Executar testes em navegadores e dispositivos reais, Lighthouse e auditoria de acessibilidade.

## Estrutura
- `public/`: interface, estilos, scripts e logos fornecidas.
- `src/server.js`: servidor HTTP/API, validação, rate limit, segurança e envio SMTP.
- `architecture/`: propósito, sistema visual e stack fixados.
- `tests/`: testes básicos do endpoint/validação.

## Limites conhecidos
O briefing não continha número de WhatsApp nem links oficiais das redes. O site não os inventa; basta definir as variáveis de ambiente para exibir os respectivos atalhos. Cases de 2026 aparecem sem nomes de clientes, como recomenda o briefing até que haja autorização.

O sitemap só é publicado quando `SITE_URL` estiver configurado com o domínio final em HTTPS. O arquivo `/.well-known/security.txt` também é servido por rota explícita.
