## Links and resources

### General programming

- [Programming Idioms](https://www.programming-idioms.org/)
  - polyglot search for common programming problems
- [Big List Of Naughty Strings](https://github.com/minimaxir/big-list-of-naughty-strings)
  - User input strings that have a high probability of causing issues
- [TLC Model Checker](https://lamport.azurewebsites.net/tla/toolbox.html)
  - a tool in the TLA+ suite for analysing specs, used by AWS as described in [[Use of formal methods at AWS]]
- [Automating Stacked PRs on GitHub](https://graphite.dev/blog/stacked-prs)
  - Service that integrates with GitHub for creating stacked PRs
- [10-minute mail](https://10minutemail.com/)
  - service that provides short-lived email addresses
- [Will Reed Top 100](https://www.willreedtop100.com/top-100-list)
  - Top 100 startups based on company culture
- [ARIA Authoring Practices Guide (APG)](https://www.w3.org/WAI/ARIA/apg/patterns/)
  - guides for implementing accessible UI patterns

### Rust

- [trust](https://github.com/japaric/trust)
  - Travis CI template for building Rust binaries for multiple OSes
- [Rust Cookbook](https://rust-lang-nursery.github.io/rust-cookbook/)
  - idiomatic solutions for common Rust tasks
- Writing web apps in Rust with webassembly:
  - [Leptos](https://leptos.dev/)
    - uses Signals for reactivity
    - Svelte/JSX-like syntax for components written in Rust
    - relies on a server implementation, such as actix
  - [Sycamore](https://sycamore-rs.netlify.app/)
    - uses Signals for reactivity
- [Shuttle.rs](https://shuttle.rs/)
  - quickly deploy Rust apps with infrastructure as code

### HTML

- [HTMLHell](https://htmlhell.com/)
  - common bad practices in HTML

### Database

- [DB Fiddle](https://www.db-fiddle.com/f/2hU2nuUrSiujYtn9eBtuXV/0)
  - JSFiddle for databases
- [SurrealDB](https://docs.surrealdb.com/docs/integration/sdks/rust/)
  - a multiplatform open-source database, written in Rust
- [Turso](https://turso.tech)
  - embedded SQLite dbs at scale
  - see [[theprimeagen]]'s interview: https://www.youtube.com/watch?v=fq2PUpgfCi4
- [Atlas](https://atlasgo.io/getting-started/)
  - Terraform-like configs for database migrations
  - see https://blog.turso.tech/database-migrations-made-easy-with-atlas-df2b259862db
- [dbdiagram](https://dbdiagram.io)
  - mermaidjs-like web interface specifically for ERDs
- [litestream.io](https://litestream.io/)
	- continuous backup of SQLite db's

## ETL

- [Airbyte](https://airbyte.com/tutorials/mysql-change-data-capture-cdc)
  - open-source ETL platform
- [Debezium](https://debezium.io/)
  - Extraction library
