# Contexto — Cartão Virtual Workin
**Última atualização:** 08/07/2026
**Agente ativo na sessão:** Orion (aiox-master) orquestrando copy-master (Cyrus) e design-squad (Design Chief)

> Para retomar este assunto: leia este arquivo inteiro antes de agir. Ele contém todo o histórico de decisões, conteúdo aprovado e o que ainda falta.

---

## 1. O que é o projeto

Cartão de visita digital da Workin, para substituir/complementar o cartão físico e servir tanto para:
- **Uso individual** — vendedores compartilhando o link pessoal em prospecção (WhatsApp, reuniões)
- **Distribuição em campanha** — divulgação mais ampla (redes, QR code)

Decidido em conjunto com o usuário: serão **2 modelos**, construídos **nesta ordem**:
1. **Institucional** (em andamento — ver status abaixo)
2. **Pessoal/Comercial** (por vendedor, com foto — ainda não iniciado)

---

## 2. Infraestrutura

| Item | Valor |
|---|---|
| Repositório GitHub | `github.com/soutotls/workin-cartao` (público) |
| Domínio (CNAME já configurado no repo) | `cartao.sistemaworkin.com.br` |
| DNS | ✅ Configurado pelo usuário — CTO ainda vai revisar/validar (sem previsão fechada) |
| GitHub Pages | ✅ Ativado via API (branch `main`, path `/`) |
| HTTPS enforced | ⏳ Ainda não ativado — fazer depois que o domínio propagar e o certificado for emitido |
| `index.html` (no ar hoje) | Placeholder "em construção" — **é o que está publicado atualmente** |

### Padrão de publicação (igual ao `workin-lp`)
Commit + `git push origin main` publica direto no GitHub Pages. Sem pipeline de build.

---

## 3. Status atual do trabalho — Modelo Institucional

**Arquivo:** `institucional.html` (nesta mesma pasta)
**Status:** ✅ Construído e ajustado visualmente · ❌ **NÃO publicado ainda** — usuário quer validar com o time inteiro antes do `git push`.

### Arquivos locais não commitados (`git status` confirma):
- `institucional.html`
- `favicon.png` (copiado de `WeSales/favicon.png`)
- `logo-workin-negativa-header.png` (copiado de `WeSales/`)
- `workin-simbolo-icon.png` (**recortado sob medida** — ver nota técnica abaixo)

### Nota técnica importante — símbolo Workin
O arquivo original (`Manual da Marca/assets/logo/RGB/workin-simbolo.png`) tem uma tela de 8001×4501px com o desenho ocupando só uma fração pequena — usar ele direto faz o símbolo aparecer minúsculo em qualquer contêiner pequeno (isso já aconteceu e foi corrigido). `workin-simbolo-icon.png` é um recrop 1:1 já centralizado e pronto para uso em avatares/ícones — **usar sempre este arquivo para esse fim, não o original**.

### Iterações de ajuste visual já feitas
1. Avatar 92px → 112px, símbolo 56px → 78px → **96px** (estado atual — o usuário pediu para chegar mais perto da borda do círculo)
2. Blobs decorativos de fundo suavizados (opacidade reduzida)
3. LinkedIn adicionado ao lado do Instagram na linha de redes sociais

---

## 4. Copy aprovada (institucional) — não alterar sem revisar com o Cyrus (copy-master)

**Eyebrow:** `Cartão Virtual`

**Headline** (reaproveita a assinatura de anúncio já validada da marca):
> Workin — o ERP que conhece o seu tipo de negócio.

**Bio:**
> Seu time opera sem treinamento longo e sem precisar entender de fiscal — com suporte humano real, de quem conhece o seu negócio, onde você estiver no Brasil.

**CTAs, nesta ordem:**
1. `💾 Salvar contato Workin` — gera `.vcf` on-the-fly via JS (Blob), sem backend
2. `💬 Falar com o Comercial` → `wa.me/5567992811252` (mensagem pré-preenchida)
3. `🛠️ Falar com o Suporte` → `wa.me/556721053900` (mensagem pré-preenchida)
4. `🌐 Conhecer o sistema` → `https://sistemaworkin.com.br`

**Redes sociais:**
- Instagram: `@sistema_workin` → `instagram.com/sistema_workin`
- LinkedIn → `https://www.linkedin.com/company/sistemaworkin/`

**Rodapé (compliance):**
> Workin — 3LMS Manutenção e Sistemas Ltda · CNPJ 24.375.944/0001-01

### Números de WhatsApp — não confundir
- **Comercial** `+55 (67) 99281-1252` — linha dedicada, uso exclusivo da equipe comercial
- **Suporte** `+55 (67) 2105-3900` — é o mesmo número "oficial" já divulgado no rodapé das LPs (telefone fixo/institucional), reaproveitado também como WhatsApp de suporte

### Dados do vCard gerado
```
BEGIN:VCARD
VERSION:3.0
N:;Workin;;;
FN:Workin - Sistema ERP
ORG:Workin (3LMS Manutenção e Sistemas Ltda)
TEL;TYPE=WORK,VOICE:+556721053900
TEL;TYPE=WORK,CELL:+5567992811252
EMAIL:oi@workin.com.br
URL:https://sistemaworkin.com.br
NOTE:Cartão Virtual Workin
END:VCARD
```

---

## 5. Decisões de squad (para não repetir o roteamento)

- **copy-master (Cyrus)** escreveu a copy institucional com **Blair Warren** (redator principal, identidade/conexão), **David Ogilvy** (revisão de tom/marca) e **Robert Cialdini** (camada de persuasão — liking + autoridade). Recomendação do Cyrus: não inventar prova social sem dado real.
- **design-squad (Design Chief)** rodou o fluxo `feature_design`: ux-designer definiu a hierarquia (avatar → badge → headline → bio → CTAs → social → rodapé), ui-engineer implementou reaproveitando os tokens de cor/tipografia já usados na calculadora IBS/CBS e nas LPs (`--accent #00AD50`, `--brand #22253A`, fonte `Segoe UI`/system-ui).
- Referência visual usada: `Manual da Marca/assets/referencias/06-aplicacao-cartao-de-visita.jpg` (cartão físico existente — faixa verde + símbolo + navy para texto).

---

## 6. Pendências / decisões em aberto

- [ ] **Validação do time** — usuário vai revisar `institucional.html` com a equipe antes de aprovar publicação (bloqueio atual — não publicar sem OK explícito)
- [ ] Decidir se o institucional vira a **home** (`cartao.sistemaworkin.com.br/`) ou fica em path próprio (`/institucional`), deixando a home livre para o cartão pessoal padrão — pergunta feita ao usuário, ainda sem resposta
- [ ] CTO ainda precisa confirmar/revisar o DNS
- [ ] Ativar "Enforce HTTPS" no GitHub Pages assim que o domínio propagar
- [ ] Iniciar o **modelo Pessoal/Comercial** (por vendedor) — só depois do institucional aprovado. Vai precisar: foto real por vendedor, nome/cargo, WhatsApp próprio (não usar Suporte), mesmo padrão de vCard e CTAs
- [ ] Testar o botão "Salvar contato" em iOS e Android de verdade (comportamento de `.vcf` via Blob pode variar entre navegadores)

---

## 7. Como retomar

1. Ler este arquivo inteiro
2. Abrir `institucional.html` local para ver o estado visual atual
3. Perguntar ao usuário: "o time já validou o institucional?" — se sim, seguir para publicação (commit + push, igual ao padrão do `workin-lp`); se não, continuar ajustando
4. Se aprovado e publicado, avançar para o modelo Pessoal/Comercial (repetir o fluxo: copy-master → design-squad)
