# InsectFlux Visibility Publish Checklist

## Goal

Make Mohamed's InsectFlux work visible without leaking private code or overclaiming team contributions.

## Assets created

- `README.md` — public-safe case study.
- `architecture.md` — public-safe architecture explanation.
- `linkedin-resume-snippets.md` — snippets for LinkedIn/resume/recruiters.

## Publish options

### Option A — GitHub public case-study repo

Create a new public repo:

`mohamedswe/insectflux-case-study`

Contents:

- README.md
- architecture.md
- no private source code
- no screenshots unless approved
- no secrets or private data

Best for: GitHub profile/pinned repo visibility.

### Option B — GitHub profile README section

Add a section to profile README:

```markdown
### InsectFlux — Backend Reliability for an Agri-Food Marketplace
One of three engineers. My ownership focused on database migrations with forward/backward compatibility, backend testing, webhook-driven messaging/payment reliability, and production hardening.
```

Best for: fastest profile signal.

### Option C — LinkedIn Featured project/post

Post the LinkedIn blurb and link to the case study repo/page.

Best for: recruiters and network visibility.

## Required approval before publishing

Before publishing, Mohamed should approve:

- wording is accurate,
- no teammate work is overclaimed,
- no private implementation details are exposed,
- whether InsectFlux name can be used publicly,
- whether screenshots are allowed,
- whether the project is okay to mention as private/team-owned.

## Commands to publish as GitHub repo after approval

From this folder:

```powershell
cd <path-to-this-folder>
git init
git add README.md architecture.md linkedin-resume-snippets.md publish-checklist.md screenshot-guide.md assets/
git commit -m "docs: add InsectFlux backend reliability case study"
gh repo create insectflux-case-study --public --source . --push --description "Backend reliability, migrations, testing, and webhook messaging case study for an agri-food marketplace"
```

Do not run this until Mohamed approves publication.
