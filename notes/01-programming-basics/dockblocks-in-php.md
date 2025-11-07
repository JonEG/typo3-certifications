# DocBlocks in PHP

→ [Back to Syllabus](../../syllabus/01-programming-basics.md#dockblocks-in-php)

## What is a DocBlock?

A DocBlock is a special PHP comment used for **documentation**, **type hinting**, and **annotations**.
It sits above classes, functions, properties, or methods.

**Syntax:**

```php
/**
 * Short description
 *
 * Long description (optional)
 *
 * @tag Description
 */
```

---

## General Purpose

* Explain **what** a class, method, or property does.
* Provide **type hints** for IDEs and static analyzers.
* Support **automatic documentation** generation.
* Enable **TYPO3 and PHP tools** (e.g., Extbase, Fluid, PHPStan).

**Limitations:**

* Not executed at runtime.
* Cannot enforce behavior—only **informational** or **annotation-based**.

---

## Common Annotations

| Annotation    | Usage Example                       | Purpose                                 |
| ------------- | ----------------------------------- | --------------------------------------- |
| `@param`      | `@param int $count Number of items` | Describes function/method parameters    |
| `@return`     | `@return string The resulting text` | Describes return type                   |
| `@var`        | `@var string $title`                | Describes property type                 |
| `@throws`     | `@throws \Exception`                | Describes exceptions a method can throw |
| `@deprecated` | `@deprecated since v13.0`           | Marks code as deprecated                |
| `@internal`   | `@internal`                         | Marks code as internal only             |
| `@author`     | `@author John Doe`                  | Author of the code                      |
| `@see`        | `@see OtherClass::method()`         | Link to related code                    |
| `@inheritdoc` | `@inheritdoc`                       | Inherit doc from parent class/method    |

**TYPO3-specific annotations:**
`@Extbase` annotations for models (`@TYPO3\CMS\Extbase\Annotation\ORM\Cascade` etc.)

---

## When to Omit DocBlocks

* **Trivial getters/setters** in classes (e.g., `getName()`, `setName()`).
* **Obvious types** fully inferred by PHP 8+ type hints.
* **Private/internal methods** with clear naming.
* Avoid redundant or misleading DocBlocks.

**Good practice:**

* Always document **public APIs** (Extbase actions, services, domain models).
* Keep short descriptions concise.
* Use **annotations only when necessary** for tooling or TYPO3 processing.

---

## Quick Example from TYPO3 13.4

 Source code here: [TYPO3 Github Repository](https://github.com/TYPO3/typo3/blob/13.4/typo3/sysext/form/Classes/Service/TranslationService.php)

 Find it locally here: [Code link](../../code/typo3-13.4/typo3/sysext/form/Classes/Service/TranslationService.php)

```php
class TranslationService implements SingletonInterface
{
    /**
     * Returns the localized label of the LOCAL_LANG key, $key.
     *
     * @param mixed $key The key from the LOCAL_LANG array for which to return the value.
     * @param array|null $arguments the arguments of the extension, being passed over to vsprintf
     * @param mixed $defaultValue
     * @return mixed The value from LOCAL_LANG or $defaultValue if no translation was found.
     * @internal
     */

    public function translate(
        $key,
        ?array $arguments = null,
        ?string $locallangPathAndFilename = null,
        ?string $language = null,
        $defaultValue = ''
    ) {
        ...
    }
}
```

---

**References and more on this topic:**

* [TYPO3 Explained 13.4 Using phpDoc](https://docs.typo3.org/m/typo3/reference-coreapi/13.4/en-us/CodingGuidelines/CglPhp/UsingPhpdoc.html#using-phpdoc)
* [PHPDoc on Wikipedia](https://en.wikipedia.org/wiki/PHPDoc)
* [phpDocumentor manual Basic Syntax](https://docs.phpdoc.org/3.0/guide/references/phpdoc/basic-syntax.html)
* [phpDocumentor manual: what is a DocBlock?](https://docs.phpdoc.org/3.0/guide/getting-started/what-is-a-docblock.html)

---
→ [Back to Syllabus](../../syllabus/01-programming-basics.md#dockblocks-in-php)
