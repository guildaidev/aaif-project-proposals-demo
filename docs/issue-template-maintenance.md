# Issue Template Maintenance Checklist

Use this checklist when changing the project proposal issue form
(`.github/ISSUE_TEMPLATE/project-proposal.yml`) or the issue chooser config
(`.github/ISSUE_TEMPLATE/config.yml`). All example commands run offline and use
repository-relative paths.

## Validation checklist

- [ ] **Both YAML files parse cleanly.** Confirm
      `.github/ISSUE_TEMPLATE/project-proposal.yml` and
      `.github/ISSUE_TEMPLATE/config.yml` are still valid YAML.
- [ ] **Required fields preserved.** Every input/textarea that had
      `validations.required: true` (Project Name, Project Description, License,
      GitHub Repository URL, contact name/email, and others) is still present
      and still required. The `trademark` checkbox option keeps `required: true`.
- [ ] **`labels` and `assignees` preserved.** The form still declares
      `labels: ["New"]` and `assignees` (`christinaharter`, `maniksurtani`).
- [ ] **`contact_links` are valid.** When `contact_links` are added to
      `.github/ISSUE_TEMPLATE/config.yml`, verify each entry has `name`, `url`,
      and `about`. (None exist yet; this is forward-looking guidance.)
- [ ] **Diff contains only intended files.** No unrelated files are changed.

## Example commands

Confirm only the intended files changed:

```sh
git status --short
git diff --stat
```

Parse-check the issue form (requires PyYAML or `yamllint` installed locally):

```sh
python3 -c "import yaml; yaml.safe_load(open('.github/ISSUE_TEMPLATE/project-proposal.yml'))"
python3 -c "import yaml; yaml.safe_load(open('.github/ISSUE_TEMPLATE/config.yml'))"
```

Confirm the template files are unchanged when only editing docs:

```sh
git diff --name-only .github/ISSUE_TEMPLATE/
```
