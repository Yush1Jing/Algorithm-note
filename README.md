# Algorithm Notes

My algorithm and LeetCode study notes, published as a website with MkDocs Material.

## Structure

- `docs/00-preface/`: preface and study plan
- `docs/01-data-structures/`: data structure basics
- `docs/02-patterns/`: algorithm patterns and templates
- `docs/03-problems/`: one page per problem, named `<LeetCode id>-<slug>.md`
- `docs/04-mistakes/`: mistakes log
- `docs/appendix/`: templates

## Local preview

```bash
pip install -r requirements.txt
mkdocs serve
```

Every push to `main` rebuilds and publishes the site through GitHub Actions.
