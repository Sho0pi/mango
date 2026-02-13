# Mango 🥭

> Money and Go — personal double-entry accounting with as little friction as
> possible.

## Philosophy

Most personal finance tools are built for the general case. But personal
accounting is almost always simpler:

1. **You have one main account** you withdraw from — no need to specify it every
   transaction.
2. **Most transactions don't need a description** — a good account hierarchy
   tells the whole story.

`expenses:food:711` is already a description.

## Usage

```bash
mango add expenses:food:711 7.1sgd
```

That's it. Mango infers the rest:

```csv
date,description,account,amount,commodity
2026-02-13,,expenses:food:711,7.10,SGD
2026-02-13,,assets:bank:ocbc360,-7.10,SGD
```

Need more detail? Use flags:

```bash
mango add expenses:food:711 7.1sgd --date 2026-02-12 --title "711 run"
```

## Data Format

Mango stores everything as plain CSV files — no database, no binary formats, no
lock-in.

```
bookkeeping/
  journal.csv    # all transactions
  accounts.csv   # account definitions
  prices.csv     # commodity prices over time
```

Plain text means your financial history is readable forever and diffs cleanly in
git.
