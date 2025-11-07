# PHP Basics and Variables

→ [Back to Syllabus](../../syllabus/01-programming-basics.md#php-basics-and-variables)

## What is PHP?

* **PHP** (Hypertext Preprocessor) is a **server-side scripting language** for web development.
* Processes code on the server and outputs **HTML, JSON, or other formats**.
* Widely used in TYPO3 for **extensions, backend modules, Fluid templates, and APIs**.

---

## Areas of Application

* Web applications (CMS, blogs, e-commerce)
* Server-side scripting (processing forms, sessions)
* APIs (REST, GraphQL)
* Command-line scripts and cron jobs

---

## Running PHP in Terminal

1. **Check version:**

```bash
php -v
```

2. **Run a script:**

```bash
php script.php
```

3. **Interactive mode (REPL):**

```bash
php -a
```

---

## Variables in PHP

* Declared with `$` followed by the name:

```php
$variableName = "value";
```

* **Dynamic typing:** PHP automatically determines the type at runtime.
* **Variable types:** string, int, float, bool, array, object, null, resource

**Example:**

```php
$name = "John";        // string
$age = 30;             // integer
$price = 19.99;        // float
$isPublished = true;   // boolean
$tags = ["php", "typo3"]; // array
```

---

## Strong vs Dynamic Typing

* **Dynamic typing (PHP default):**

  * Type is inferred at runtime.
  * Example:

  ```php
  $x = 5;    // int
  $x = "5";  // string, allowed
  ```

* **Strong typing (optional in PHP 7+):**

  * Enforce type hints in functions, return types, and declare(strict_types=1)

  ```php
  declare(strict_types=1);

  function add(int $a, int $b): int {
      return $a + $b;
  }
  ```

---

## Tips for TYPO3 Developers

* Always use **type hints** in Extbase models and controllers.
* Use **PHP 8 type declarations** for properties and methods for clarity.
* Dynamic typing is flexible but can hide bugs; strong typing improves safety.

---

**References:**

* [PHP Manual](https://www.php.net/manual/en/)
* [TYPO3 v13 Core API](https://docs.typo3.org/)

---
→ [Back to Syllabus](../../syllabus/01-programming-basics.md#php-basics-and-variables)
