# 🌊 SurfCast — Estudo de Caso de Arquitetura em Produção

## Visão Geral

O SurfCast é um ecossistema completo desenvolvido para entregar previsões inteligentes de surf, relatórios operacionais em tempo real, análise contextual via inteligência artificial e monetização integrada.

A plataforma foi concebida como um produto digital completo que combina dados oceanográficos, inteligência artificial, geolocalização e feedback operacional de surfistas em campo.

Este projeto foi desenvolvido através de um fluxo de **desenvolvimento assistido por IA (AI-assisted development)**, onde atuei diretamente na concepção do produto, arquitetura do sistema, definição de regras de negócio, integrações, decisões de infraestrutura e evolução contínua.


### - aplicativo na google store
https://play.google.com/store/apps/details?id=br.com.mbarozzi.rj_surfcast&hl=pt_BR

### - videos
https://www.youtube.com/watch?v=F50k_8TI_Rs&t=14s

https://www.youtube.com/watch?v=F50k_8TI_Rs&t=14s


---

# O Problema

Aplicativos tradicionais de previsão de surf normalmente entregam apenas dados técnicos brutos.

Isso gera alguns problemas:

* Dificuldade na interpretação de swell, vento e maré
* Falta de contexto local
* Ausência de correção baseada na condição real do mar
* Pouca personalização
* Falta de inteligência operacional em tempo real

O SurfCast foi criado para resolver essas limitações.

---

# A Solução

O SurfCast transforma dados técnicos em inteligência prática para o surf através de três camadas integradas:

* Motor de Inteligência Backend
* Camada Mobile
* Engine de Monetização e Controle de Acesso

---

# Arquitetura Geral

```text
Stormglass API
       ↓
RJ Surfcast API (Django)
       ↓
 ┌──────────────┬──────────────┬──────────────┐
 ↓              ↓              ↓
IA              Relatos        Ads Engine
(Ollama/OpenAI) Operacionais   (Monetização)
       ↓
App Flutter
       ↓
Usuário Final
```

---

# Backend — RJ Surfcast API

O backend é o núcleo central de inteligência da plataforma.

Construído com:

* Django
* PostgreSQL
* REST API
* FFmpeg
* Infraestrutura VPS

---

## Core Engine

Responsável por:

### Processamento de Previsões

* Coleta automatizada de previsões marítimas via Stormglass
* Processamento de altura das ondas
* Período de swell
* Intensidade do vento
* Direção do vento
* Comportamento das marés

---

## Algoritmo Proprietário de Classificação

Um dos principais diferenciais do produto.

O sistema cruza múltiplas variáveis para gerar:

* Qualificação das ondas
* Sistema de estrelas (1 a 5)
* Ranking inteligente de condições

Isso transforma dados técnicos complexos em decisões práticas.

---

## Sistema de Praias Próximas

Motor baseado em geolocalização:

* Captura do GPS do usuário
* Cálculo de distância
* Filtro de praias elegíveis
* Ordenação por qualidade ou proximidade

---

# Engine de Inteligência Artificial

O SurfCast integra modelos LLM através de:

* Ollama (inferência local/privada)
* OpenAI (fallback em nuvem)

A IA não responde de forma genérica.

Ela recebe contexto baseado em:

* Praia selecionada
* Previsões atuais
* Classificação das ondas
* Comportamento do vento
* Status da maré
* Histórico de relatos operacionais

Isso gera respostas altamente contextualizadas.

---

# Autenticação e Segurança

Sistema próprio de usuários com:

* Login por e-mail e senha
* Confirmação de cadastro por e-mail
* Recuperação de senha
* Bloqueio de domínios temporários
* Gestão de credenciais para homologação em lojas

Camada desenhada pensando em produção e validação.

---

# Sistema de Relatos Operacionais

Um dos pontos mais fortes do produto.

Usuários autorizados podem enviar:

* Condições reais do mar
* Nota técnica de impacto (-5 a +5)
* Vídeos em tempo real

Esses relatos modificam dinamicamente as classificações das previsões.

Modelo híbrido:

Previsão matemática + Inteligência humana em campo

---

# Arquitetura Híbrida de Upload de Vídeo

Suporte para:

* Armazenamento local
* Armazenamento externo
* Estratégia híbrida

Com integração de:

* Corte automático com FFmpeg
* Sobrescrita de vídeos antigos
* Priorização de relatos ativos
* Ocultação temporal de vídeos antigos

---

# Engine de Monetização

Sistema modular independente para monetização.

Desenvolvido como pacote Flutter separado.

Recursos:

* Rotação dinâmica de anúncios
* Controle persistente anti-repetição
* Banners
* Vídeos patrocinados
* Métricas de visualização e clique
* Controle de acesso à IA

Modos:

* Premium
* Trial
* Acesso patrocinado

---

# Aplicativo Mobile — Flutter

Camada de experiência final do usuário.

Funcionalidades:

* Mapa interativo de praias
* Dashboard de previsões
* Chat com IA
* Gráficos de evolução das ondas
* Painéis de maré
* Praias próximas
* Ranking de melhores condições
* Relatos operacionais
* Player de vídeos

Tudo integrado diretamente ao backend.

---

# Infraestrutura

Infraestrutura atual em produção:

## Servidor Principal

Hostinger VPS

Responsável por:

* API
* Banco de dados
* Autenticação
* Regras de negócio

---

## Servidor de IA

InterServer VPS

Responsável por:

* Execução do Ollama
* Inferência de modelos LLM
* Processamento de prompts

---

## Estratégia de Storage

Arquitetura híbrida para:

* Persistência local
* Persistência externa
* Fallback automático

Projetado para escalabilidade e redução de custos.

---

# Desafios Técnicos Resolvidos

* Correção dinâmica de previsões em tempo real
* Roteamento híbrido de IA
* Controle remoto de updates do app
* Escalabilidade de vídeos
* Rotação persistente de anúncios
* Credenciais para revisão de lojas
* Bloqueio de abuso com e-mails temporários
* Fallback de upload híbrido

---

# Status Atual do Produto

Situação atual:

✅ Ambiente de produção ativo
✅ Publicação na Google Play ativa
✅ Backend em operação
✅ IA em operação
✅ Monetização ativa
✅ Evolução contínua em andamento

---

# Minha Atuação

Este projeto foi desenvolvido através de AI-assisted development.

Minhas responsabilidades incluem:

* Concepção do produto
* Arquitetura do sistema
* Definição de regras de negócio
* Orquestração backend
* Estratégia de infraestrutura
* Integrações externas
* Fluxos de IA
* Estratégia de monetização
* Deploy em produção
* Evolução contínua

---

# Stack Tecnológica

Backend:

* Django
* PostgreSQL
* REST API

Mobile:

* Flutter

IA:

* Ollama
* OpenAI

Infraestrutura:

* VPS
* Storage híbrido

Serviços externos:

* Stormglass

Processamento de mídia:

* FFmpeg

---

# Roadmap Futuro

Próximas evoluções:

* Versão iOS
* Expansão para novas regiões
* Personalização avançada com IA
* Assinaturas premium
* Inteligência ampliada para vídeos
* Alertas automáticos de surf
* Ranking comunitário de relatos

---

O SurfCast não é apenas um aplicativo de previsão.

É uma plataforma de inteligência operacional para surf.
