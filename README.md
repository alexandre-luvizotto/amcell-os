<h1 align="center">📱 AM CELL OS</h1>
<p align="center"><b>Sistema de Ordens de Serviço para assistências técnicas de celulares</b><br>
SaaS em produção · PHP 8.3 · MySQL · PWA</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-em%20produ%C3%A7%C3%A3o-brightgreen?style=flat-square">
  <img src="https://img.shields.io/badge/PHP-8.3-777BB4?style=flat-square&logo=php&logoColor=white">
  <img src="https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white">
  <img src="https://img.shields.io/badge/PWA-instal%C3%A1vel-5A0FC8?style=flat-square&logo=pwa&logoColor=white">
  <img src="https://img.shields.io/badge/LGPD-adequado-0A66C2?style=flat-square">
</p>

🔗 **No ar:** [amcell.lvztech.com.br](https://amcell.lvztech.com.br)

---

## 🎯 O problema

Assistências técnicas pequenas costumam controlar ordens de serviço em papel ou WhatsApp. Isso gera três dores: **disputa com cliente** sobre o estado em que o aparelho chegou, **cliente ligando o tempo todo** para saber se ficou pronto e **falta de controle** de estoque e caixa.

## ✅ A solução

Um sistema web instalável no celular (PWA) que a loja usa no balcão:

- **Entrada do aparelho com fotos pela câmera do celular** — frente, verso, laterais, conector e tela — registradas como prova do estado de entrada; fotos de **saída** na devolução.
- **Cadastro do cliente** (nome, CPF, celular) com **histórico** de atendimentos.
- **Link de acompanhamento** para o cliente ver o status em tempo real: *em andamento → em testes → concluído*.
- **Comprovante em PDF** com serviço realizado, horário, valor, desconto e dados da loja.
- **Envio por WhatsApp** com mensagem pronta de "seu celular está pronto".
- **Estoque com baixa automática** de peças usadas na OS.
- **Financeiro** (entradas, saídas, caixa).
- **Equipe** com perfis e permissões por usuário.
- Edição e cancelamento de OS com registro.
- **Multi-loja**: vendido para outras assistências em planos **Mensal** e **Vitalício**, com contas liberadas pelo administrador.

## 🏗️ Arquitetura

```
Navegador / PWA (celular do técnico)
        │  HTTPS
        ▼
Servidor PHP 8.3 (Hostinger)
  ├── Autenticação e sessões
  ├── Controle de acesso por perfil (admin / técnico / atendente)
  ├── Módulos: OS · Clientes · Estoque · Financeiro · Equipe
  ├── Geração de PDF do comprovante
  └── Upload e armazenamento das fotos do aparelho
        │
        ▼
MySQL (dados isolados por loja)
```

## 🔐 Segurança e LGPD

- Senhas armazenadas com **hash**, nunca em texto puro.
- Consultas ao banco com **prepared statements** (proteção contra SQL Injection).
- Validação de dados no **servidor**, não só no navegador.
- Saída escapada contra **XSS**.
- Separação de dados **por loja** (um cliente nunca vê dados de outro).
- Tela e regras de **LGPD**: finalidade dos dados, consentimento e tratamento de CPF e fotos.
- Credenciais do banco fora do código-fonte.

## 🧠 Decisões técnicas

| Decisão | Por quê |
|---|---|
| PHP 8.3 + MySQL na hospedagem compartilhada | Já disponível no plano atual, custo zero de infraestrutura extra e deploy simples |
| PWA em vez de app nativo | Instala no celular sem loja de aplicativos e acessa a câmera direto pelo navegador |
| Subdomínio `amcell.lvztech.com.br` | Mantém o site institucional e o sistema independentes no mesmo domínio |
| WhatsApp manual com mensagem pronta | Evita custo e bloqueios da API oficial, mantendo um clique para o atendente |

## 🗺️ Roadmap

- [x] Servidor, banco e autenticação
- [x] OS com câmera, comprovante, WhatsApp e link do cliente
- [x] Estoque e financeiro
- [x] Equipe, clientes, LGPD, edição/cancelamento de OS
- [ ] Garantia no comprovante
- [ ] Relatórios
- [ ] Emissão de nota fiscal (NFS-e / NFC-e)

## 👤 Autor

**Alexandre Luvizotto** — Fundador da [LVZTECH](https://lvztech.com.br) · Estudante de ADS (Unicesumar)
📧 suportelvztech@gmail.com · 💬 [WhatsApp](https://wa.me/5541991950582)

> Produto comercial: este repositório apresenta o projeto. O acesso ao código-fonte pode ser liberado para avaliação técnica mediante solicitação.
