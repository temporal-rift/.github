<div align="center">
  <a href="https://github.com/temporal-rift">
    <img src="https://raw.githubusercontent.com/temporal-rift/docs/master/logo.png" alt="Temporal Rift" width="420">
  </a>

  <p><strong>Influence the past. Control the future. Don't reveal yourself.</strong></p>

  <p>
    A hidden-faction strategy game for 3–5 players<br>
    45–75 minutes · ages 14+
  </p>

  <p>
    <a href="https://github.com/temporal-rift/docs/blob/master/game-design/overview.mdx"><strong>How to play</strong></a>
    ·
    <a href="https://github.com/temporal-rift/docs/blob/master/game-design/factions.mdx">The five factions</a>
    ·
    <a href="https://github.com/temporal-rift/docs/tree/master/game-design">Full rules</a>
  </p>
</div>

## Everyone wants a different ending

You are a time traveler with a secret faction and a private agenda. Every era, the future is
laid out before it happens: three events, each with three possible outcomes. You hold a private
hand of cards and three faction specials, and you play them into the past to push an outcome,
suppress it, or collide two futures together.

Nobody at the table knows who you serve — until your plays give you away. Contradictory actions
raise paradoxes that stall the era until they are resolved. Ignore three, and the timeline
collapses.

## The five factions

| Faction | What they want | How they win |
| --- | --- | --- |
| **Erasers** | Wipe outcomes out of existence | Annihilate 4+ leading outcomes, or 20 points |
| **Prophets** | The future resolves as written | 3+ written outcomes win, or 20 points |
| **Revisionists** | A secret outcome, chosen fresh each era | Their secret outcome wins 3+ eras, or 20 points |
| **Weavers** | One unbroken chain of cause | Complete a chain of 4 connected events, or 20 points |
| **Activists** | Public declarations that come true | 3+ correct declarations in a row, or 20 points |

## An era, in five beats

1. **Future revealed** — one event per player, three outcomes each, all starting at 33%.
2. **Declarations** — an Activist may commit to an outcome publicly before the first round.
3. **Action rounds** — three sealed rounds, one card or one special each. Information widens as the era goes on.
4. **Paradox check** — contradictions open a paradox; everyone plays a Stabilize or Detonate card.
5. **Outcome** — probabilities decide the winners, scores move, the next era begins.

A game ends at 20 points, after five eras, or when a third cascade collapses the timeline —
victory for the Erasers and Revisionists, defeat for everyone else.

## Read the design

- [Game design](https://github.com/temporal-rift/docs/tree/master/game-design) — factions, cards, eras, probability, paradoxes, scoring
- [Sagas](https://github.com/temporal-rift/docs/tree/master/sagas) — how a round resolves, down to the individual actions

<details>
<summary><strong>For developers</strong> — services, stack and source</summary>

The game is also a production-grade, event-driven system: domain-driven design, CQRS, event
sourcing, sagas and the transactional outbox pattern, across three independently deployable
services that talk only through Kafka.

| Repository | Purpose |
| --- | --- |
| [`game-service`](https://github.com/temporal-rift/game-service) | Game orchestration, sessions, player actions, and scoring |
| [`timeline-service`](https://github.com/temporal-rift/timeline-service) | Event-sourced timeline resolution and paradox handling |
| [`read-service`](https://github.com/temporal-rift/read-service) | CQRS projections and player-facing game-state queries |
| [`game-client`](https://github.com/temporal-rift/game-client) | The browser gameplay client |
| [`apis`](https://github.com/temporal-rift/apis) | Spec-first REST and event contracts |
| [`infrastructure`](https://github.com/temporal-rift/infrastructure) | Local platform stack and end-to-end verification |
| [`simulation-workbench`](https://github.com/temporal-rift/simulation-workbench) | Reproducible experiments and balance analysis for designers |
| [`temporal-rift-bom`](https://github.com/temporal-rift/temporal-rift-bom) | Shared Java build, quality, and dependency conventions |
| [`docs`](https://github.com/temporal-rift/docs) | Game design, architecture, API, event, and saga documentation |

`Java 26` · `Spring Boot 4` · `Spring Modulith` · `Apache Kafka` · `PostgreSQL` · `Liquibase` ·
`OpenAPI` · `AsyncAPI` · `Docker Compose`

```bash
git clone https://github.com/temporal-rift/infrastructure.git
cd infrastructure
docker compose up --build
```

Service development requires Java 26 and Maven 3.9.13 or newer. See each repository's README
for its focused build and workflow.

</details>

## Status

Temporal Rift is under active development — factions, cards and rules are still being tuned.
If you would like to follow along or contribute, the documentation and the open issues in each
repository are the place to start.
