# Minhas Finanças — guia de instalação

App para lançar valores **recebidos**, **pagos** e **transferências** entre bancos (Nubank, Banco do Brasil, Caixa, C6, Cora PJ e quantos mais você quiser), com contas mensais e relatórios semanais/mensais. Funciona no Android e no iPhone, inclusive sem internet.

## Arquivos (todos devem ficar juntos na mesma pasta)
- `index.html` — o app
- `manifest.json` — nome e ícone do app instalado
- `sw.js` — faz o app abrir offline
- `icon-180.png`, `icon-192.png`, `icon-512.png` — ícones

---

## Passo 1 — Colocar o app no ar (grátis, com HTTPS)

O app precisa de um endereço **https://** — a criptografia do navegador só funciona em conexão segura. O GitHub Pages fornece isso de graça.

1. Crie uma conta em https://github.com (pode ser pelo celular ou computador).
2. Clique em **New repository** (Novo repositório).
3. Em *Repository name* escreva: `seuusuario.github.io` (troque `seuusuario` pelo seu nome de usuário do GitHub).
4. Marque **Public** e clique em **Create repository**.
5. Na página do repositório, clique em **Add file → Upload files** e arraste **todos os arquivos** desta pasta (menos este LEIA-ME, se quiser). Clique em **Commit changes**.
6. Vá em **Settings → Pages** e confirme que está publicando a partir da branch `main`.
7. Aguarde alguns minutos e abra `https://seuusuario.github.io` no navegador.

> **O repositório público expõe só o código do app, não os seus dados.** Seus lançamentos nunca saem do seu celular.

## Passo 2 — Instalar no iPhone
1. Abra o endereço no **Safari**.
2. Toque no botão **Compartilhar** (quadrado com seta para cima).
3. Role e toque em **Adicionar à Tela de Início**. Se aparecer a opção **Abrir como app web**, deixe marcada.
4. Toque em **Adicionar**. O ícone "Finanças" aparece na tela inicial.

## Passo 3 — Instalar no Android
1. Abra o endereço no **Chrome**.
2. Toque nos **três pontinhos** (⋮) no canto superior.
3. Toque em **Instalar app** ou **Adicionar à tela inicial → Instalar**.

## Passo 4 — Primeiro uso
1. Abra o app pelo ícone e **crie sua senha** (mínimo 8 caracteres). **Anote-a em local seguro: não há recuperação.**
2. Toque em ⚙︎ → em cada banco, informe o **saldo inicial** (o saldo de hoje que aparece no app do banco).
3. Em **Contas**, cadastre as contas mensais (aluguel, internet, DAS, cartão, etc.) com o dia de vencimento.
4. Use o botão **+** para lançar: *Paguei* (de qual banco saiu), *Recebi* (em qual banco entrou) ou *Transferi* (de um banco para outro).

---

## Segurança — como seus dados estão protegidos
- **Ficam só no seu aparelho.** Não há servidor, login online nem envio de dados para ninguém. Uma regra de segurança (CSP) bloqueia o app de se conectar a qualquer outro site.
- **Criptografados com AES-256-GCM.** A chave é gerada a partir da sua senha com PBKDF2-SHA256 e 600.000 iterações (recomendação atual da OWASP). Sem a senha, o conteúdo salvo é ilegível.
- **Trava automática** após 5 minutos sem uso, ou quando você sai do app por mais de 1 minuto. O botão 🔒 trava na hora.
- **Conteúdo borrado** quando o app vai para segundo plano (protege a prévia na troca de apps).
- **Proteção contra tentativas:** após 5 senhas erradas, o app espera cada vez mais antes de aceitar nova tentativa.
- **Backup criptografado:** o arquivo de backup só abre com a senha.

### Cuidados que dependem de você
- Use uma senha forte que você não usa em outros lugares.
- Mantenha o **bloqueio de tela do celular** (Face ID, digital ou senha) ativado.
- **Faça backup toda semana** (⚙︎ → Salvar backup) e guarde no Drive/iCloud. Se o celular for perdido ou os dados do navegador forem apagados, o backup é a única forma de recuperar.
- Planilhas (CSV) e PDFs exportados dos relatórios **não são criptografados** — guarde-os com o mesmo cuidado de um extrato bancário.
- Os dados de cada aparelho são separados (o app não sincroniza entre celular e iPhone). Para passar de um para outro, use Salvar backup → Restaurar backup.

## Atualizar o app no futuro
Envie os arquivos novos ao repositório (Upload files) e, no `sw.js`, aumente o número da versão (`minhas-financas-v2` → `v3`). Seus dados não são afetados.
