# CiberSaúde — Mapa Interativo América do Sul

Mapa interativo de ataques cibernéticos (confirmados e alegados) contra hospitais,
operadoras e laboratórios de saúde na América do Sul (2025–2026).

Publicado em: <a href="https://saude.freitasthiago.com.br/">https://saude.freitasthiago.com.br/</a>

## Estrutura do projeto

```
index.html    → site completo (HTML, CSS e JS em um único arquivo)
vercel.json   → configuração de deploy no Vercel
```

## Como atualizar os dados

Todos os incidentes ficam no array `incidents` dentro do `index.html`,
a partir da linha que contém `const incidents = [`.

Cada incidente segue este modelo:

```js
{
  id: 11,                              // número sequencial único
  institution: "Nome da Instituição",
  type: "hospital",                    // hospital | operadora | laboratorio | software | prefeitura | governo
  city: "Cidade",
  state: "UF",                         // sigla do estado, ou "" se não aplicável
  country: "Brasil",                   // Brasil | Argentina | Colômbia | Peru | etc.
  region: "Sudeste",                   // região ou cidade capital do país
  lat: -00.0000, lng: -00.0000,        // coordenadas para o mapa (Google Maps pode ajudar)
  date: "2026-03-01",                  // formato YYYY-MM-DD (usado para ordenação)
  dateDisplay: "Mar 2026",             // texto exibido no card
  types: ["ransomware"],               // ransomware | vazamento | paralisacao | supply-chain
  severity: "high",                    // critical | high | medium | low
  group: "NomeDoGrupo",
  confirmed: false,                    // true = confirmado pela vítima | false = apenas alegado
  statusLabel: "Alegado",              // "Confirmado" ou "Alegado"
  impacts: ["dados"],                  // dados | exames | internacao
  impactTags: ["Texto curto do impacto"],
  description: "Descrição do incidente em 2-3 frases.",
  source: "https://link-da-fonte.com",
  sourceName: "Nome da Fonte"
}
```

## Deploy no Vercel

1. Faça as edições no `index.html`
2. Commit e push para o GitHub:
   ```bash
   git add index.html
   git commit -m "Adiciona incidente: Nome da Instituição"
   git push
   ```
3. O Vercel atualiza o site automaticamente em ~30 segundos.

## Fontes utilizadas

DeXpose · Ransomware.live · BreachSense · Resecurity · TecMundo · G1 ·
Clarín · INCIBE-CERT · TechNadu · BlackFog · Infosecurity Magazine
