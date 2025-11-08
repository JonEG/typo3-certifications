# PHP Code Style Tools

→ [Back to Readme](../../README.md#15-software-quality)

This skill covers tools for automatic code formatting in PHP.

Goals:

- [ ] I know about standard tools for code formatting in PHP.
- [ ] I know how to use the tools.
- [ ] I know how to integrate the tools into workflows like CI Pipelines.

## Standard Tools

| Tool | Purpose | Notes |
|---|---|---|
| **PHP-CS-Fixer** | Automatic code formatting | TYPO3 Core uses it. Highly configurable via `.php-cs-fixer.php`. |
| **PHP_CodeSniffer (phpcs & phpcbf)** | Detects (phpcs) & fixes (phpcbf) coding style issues | Uses rulesets like PSR-12 or custom TYPO3 standards. |
| **composer normalize** | Normalizes `composer.json` formatting | Often used in CI to enforce consistent dependency definitions. |
| **EditorConfig** | Cross-editor formatting consistency | Place `.editorconfig` in project root. |

## Using the Tools

### PHP-CS-Fixer

```bash
composer require --dev friendsofphp/php-cs-fixer

# Run fixer on project
vendor/bin/php-cs-fixer fix
```

### PHP_CodeSniffer

```bash
composer require --dev squizlabs/php_codesniffer

# Check style
vendor/bin/phpcs --standard=PSR12 src

# Auto-fix
vendor/bin/phpcbf src
```

### TYPO3-Specific Sniff Standard

```bash
vendor/bin/phpcs --standard=TYPO3CMS src
```

## Typical Config Files

### `.php-cs-fixer.php` (example)

```php
<?php

$finder = PhpCsFixer\Finder::create()->in(__DIR__.'/src');

return (new PhpCsFixer\Config())
    ->setRules(['@PSR12' => true])
    ->setFinder($finder);
```

### `.editorconfig` (example)

```
[*]
indent_style = space
indent_size = 4
charset = utf-8
insert_final_newline = true
```

## CI/CD Integration

### GitHub Actions Example

```yaml
name: Code Style
on: [push, pull_request]

jobs:
  php-cs-fixer:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: shivammathur/setup-php@v2
        with:
          php-version: '8.2'
      - run: composer install
      - run: vendor/bin/php-cs-fixer fix --dry-run --diff
```

### GitLab CI Example

```yaml
code_style:
  stage: test
  script:
    - composer install
    - vendor/bin/php-cs-fixer fix --dry-run --diff
```

## Best Practices

- Run formatting locally **before committing**.
- Use **pre-commit hooks** for immediate feedback.
- Ensure CI rejects formatting violations.
- Align your formatting rules with **team/project standards**.

**References and more on this topic:**

- [GitHub: PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer)
- [PHP Coding Standards Fixer Website](https://cs.symfony.com/)

---
→ [Back to Readme](../../README.md#15-software-quality)
