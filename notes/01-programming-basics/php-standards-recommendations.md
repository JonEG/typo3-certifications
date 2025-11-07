# PHP Standards Recommendations

→ [Back to Syllabus](../../syllabus/01-programming-basics#php-standards-recommendations)

## What Are PSRs?

**PSR** stands for **PHP Standards Recommendation**. They define coding standards and common interfaces that PHP projects and frameworks can follow to ensure **interoperability** and **consistent code quality**.

---

## Who Creates PSRs?

* Developed and maintained by the **PHP-FIG** (PHP Framework Interoperability Group).
* Members include representatives from major PHP projects such as TYPO3, Symfony, Laravel, Drupal, Composer, etc.
* Goal: Standardize best practices across the PHP ecosystem.

---

## Why PSRs Matter

| Benefit                   | Explanation                                               |
| ------------------------- | --------------------------------------------------------- |
| **Consistency**           | Makes code more predictable across projects.              |
| **Interoperability**      | Allows libraries, frameworks, and tools to work together. |
| **Maintainability**       | Easier for developers to read and understand code.        |
| **Tooling Compatibility** | Linters, IDEs, and autoformatters support PSRs directly.  |

---

## Key PSRs (Relevant for TYPO3)

| PSR        | Category                    | Purpose                                         | TYPO3 Relevance                                               |
| ---------- | --------------------------- | ----------------------------------------------- | ------------------------------------------------------------- |
| **PSR-1**  | Basic Coding Standard       | Core coding rules                               | Base level expectation (covered by PSR-12)                    |
| **PSR-3**  | Logging Interface           | Standardized logging API                        | **Used extensively** via `Psr\Log\LoggerInterface`            |
| **PSR-4**  | Autoloading                 | Defines class autoloading structure             | **Used by TYPO3 extensions**                                  |
| **PSR-6**  | Caching Interface           | Standard caching contracts                      | TYPO3 core provides adapters and integrates with PSR-6 caches |
| **PSR-7**  | HTTP Message Interface      | Request/Response objects                        | TYPO3 request/response objects are PSR-7 compatible           |
| **PSR-11** | Container Interface         | Standard DI container interface                 | TYPO3's DI container is PSR-11 compliant                      |
| **PSR-12** | Extended Coding Style Guide | Formatting and structure rules                  | **Preferred style in TYPO3 v13**                              |
| **PSR-14** | Event Dispatcher            | Standard event dispatching                      | TYPO3 uses PSR-14 for signals/events                          |
| **PSR-15** | HTTP Handlers / Middleware  | Middleware request handling                     | TYPO3 uses PSR-15 middleware pipeline                         |
| **PSR-16** | Simple Cache                | Simpler caching interface (single-method cache) | Libraries may support it; TYPO3 core prefers PSR-6            |
| **PSR-17** | HTTP Factories              | Factories for PSR-7 objects                     | TYPO3 provides PSR-17 factories                               |
| **PSR-18** | HTTP Client                 | HTTP client interface                           | TYPO3 exposes a PSR-18 compatible HTTP client                 |

---

## TYPO3: Which PSRs to care about

For everyday TYPO3 v13 development focus on these **must-know** PSRs:

* **PSR-3, PSR-4, PSR-6, PSR-7, PSR-11, PSR-12, PSR-14, PSR-15, PSR-17, PSR-18**.

Notes:

* **PSR-16** (Simple Cache) is implemented by some libraries, but TYPO3 core centers on PSR-6.
* **PSR-13** (Hypermedia Links) and **PSR-20** (Clock) are not relevant to TYPO3 core as of v13.

## Example: PSR-4 Autoloading Structure

```shell
composer.json → "Vendor\\Extension\\": "Classes/"
Classes/
  Controller/
  Domain/
  Service/
```

---

## Example: PSR-3 Logger Usage

```php
use Psr\Log\LoggerInterface;

class MyService
{
    public function __construct(private LoggerInterface $logger) {}

    public function doSomething(): void
    {
        $this->logger->info('Action executed.');
    }
}
```

---

## Summary

* PSRs define **shared programming standards** for PHP.
* Maintained by **PHP-FIG**, representing major PHP projects.
* Benefits include interoperability, maintainability, and consistency.
* **TYPO3 aligns primarily with PSR-12, PSR-4, and PSR-3**.

---

**References:**

* [https://www.php-fig.org/psr/](https://www.php-fig.org/psr/)
* [https://docs.typo3.org](https://docs.typo3.org/)

---

→ [Back to Syllabus](../../syllabus/01-programming-basics#php-standards-recommendations)
