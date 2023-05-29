# PHP Coding Standard

## Overview

Following coding standards is crucial to maintaining the quality, consistency, and readability of the codebase in any programming project, especially when working in a team. This consistency makes it easier for multiple developers to understand and modify the code, thus improving the efficiency of the whole team.

In the case of PHP, the PHP Framework Interop Group (PHP-FIG) has created a series of recommendations known as PHP Standard Recommendations (PSRs). These recommendations define coding standards that many PHP projects adhere to. Here are some examples of PHP coding standards following these guidelines:

## 1. Code Organization

- **PSR-0 Autoloading Standard:** This standard ensures that classes, interfaces, or traits can be loaded automatically by adhering to a specific file and directory structure.
- **PSR-4 Autoloading Standard:** This is an improved and more flexible version of PSR-0, defining a standardized way to autoloading classes from file paths.

## 2. Code Formatting

- **PSR-1 Basic Coding Standard:** This sets a series of basic rules that enforce things like using `<?php` or `<?=`, ensuring that files either define symbols or cause side-effects, but not both, etc.
- **PSR-2 Coding Style Guide:** This guide expands on PSR-1 to define a coding style guide, including rules about indentation, line length, keywords, etc.
- **PSR-12 Extended Coding Style Guide:** This is an extension of PSR-2, providing additional guidelines on declaring return types, nullable types, etc.

## 3. Coding Best Practices

- **PSR-3 Logger Interface:** This standard provides an interface for logging libraries, allowing interoperability between different logging libraries.
- **PSR-7 HTTP Message Interface:** This describes a common interface for HTTP messages, both requests and responses, as per HTTP standards.
- **PSR-11 Container Interface:** This defines a standardized interface for dependency injection containers, which are used to manage class dependencies.

In addition to these PSRs, there are numerous other coding standards that should be followed:

## 4. Naming Conventions

- Class names should be declared in `StudlyCaps`.
- Method names should be declared in `camelCase`.
- Class constants should be declared in `ALL_UPPER_CASE_WITH_UNDERSCORES`.

## 5. Indentation and Whitespace

- Code should be indented with 4 spaces, not tabs.
- There should be no trailing whitespace at the end of lines.
- There should be exactly one blank line at the end of each file.

## 6. Control Structures

- There should be one space after the control structure keyword before the opening parenthesis.
- There should be no space after the opening parenthesis or before the closing parenthesis in the control structure.
- Control structures should have their opening brace on the same line, and the closing brace on a new line.

## 7. Function Calls

- Function calls should have no spaces between the function name, the opening parenthesis, and the first parameter; spaces between commas and the next parameter, and no space between the last parameter, the closing parenthesis, and the semicolon.

## 8. Classes and Methods

- Opening braces for classes and methods must go on the next line, and closing braces must go on the next line after the body.
- Visibility must be declared on all properties and methods; `abstract` and `final` must be declared before the visibility; `static` must be declared after the visibility.

## 9. Commenting

- Code should be well-commented with single-line (`//`) and multi-line (`/* */`) comments as appropriate.
- [DocBlocks](https://docs.phpdoc.org/3.0/guide/getting-started/what-is-a-docblock.html#what-is-a-docblock) (`/** */`) should be used to provide metadata about the program elements such as classes, methods, properties, etc.

## 10. Error Reporting

- All PHP errors, warnings, and notices should be turned on by setting `error_reporting(E_ALL)`. This helps catch potential issues in the code.

## Note

Remember, these are standards and best practices, not laws. They should be used to promote consistency across your codebase, and can be adapted based on your team's preferences. However, any deviations from the standards should be well-documented and uniformly applied across the codebase.

## PHP Code Examples

Below are 30 examples of PHP code that follow good coding standards and practices. These examples adhere to **PSR-1**, **PSR-2**, and **PSR-12**.

## 1. PHP Tag

Always use full PHP tags.

    ```php
    <?php
    echo 'Hello, World!';
    ?>
    ```

## 2. Encoding

Use UTF-8 without BOM.

    ```php
    // File encoded in UTF-8 without BOM
    ```

## 3. Side Effects

A file should declare symbols (classes, functions, constants, etc.) or cause side-effects (e.g. generate output, change .ini settings, etc.) but should not do both.

    ```php
    // File with declarations
    class MyClass {
        const MY_CONST = 'Hello, World!';
        public function myFunction() {}
    }
    ```

## 4. Namespace and Class Names

Use StudlyCaps (a.k.a. PascalCase) for namespaces and class names.

    ```php
    namespace MyNamespace;
    class MyClass {}
    ```

## 5. Class Constants, Properties, and Methods

Class constants should be declared in all upper case with underscore separators. Properties and method names should use camelCase.

    ```php
    class MyClass {
        const MY_CONSTANT = 'Constant value';
        public $myProperty;
        public function myMethod() {}
    }
    ```

## 6. Indentation

Code should be indented with 4 spaces, not tabs.

    ```php
    if ($a === $b) {
        echo 'A equals B';
    }
    ```

## 7. Line Length and Whitespace

Avoid exceeding 80 characters where possible. A soft limit of 120 should be observed. There should be no trailing whitespace at the end of lines.

## 8. Keyword and True/False/Null

PHP keywords must be in lower case. The constants `true`, `false`, and `null` must be in lower case.

    ```php
    if (true) {
        echo 'True!';
    }
    ```

## 9. Control Structures

There should be one space after the control structure keyword, a space after opening parenthesis, and a space before closing parenthesis.

    ```php
    if ($a === $b) {
        echo 'A equals B';
    } else {
        echo 'A does not equal B';
    }
    ```

## 10. Function Calls

There should be no spaces between the function name and opening parenthesis, and no space between parentheses and parameters.

    ```php
    echo('Hello, World!');
    ```

## 11. Function and Class Braces

Opening braces for classes and methods must go on the next line, and closing braces must go on the next line after the body.

    ```php
    class MyClass {
        public function myFunction()
        {
            // Some code
        }
    }
    ```

## 12. Visibility and Ordering

[Visibility](https://www.php.net/manual/en/language.oop5.visibility.php) must be declared on all properties and methods. Abstract and Final must be declared before the visibility. Static must be declared after the visibility.

    ```php
    class MyClass {
        final public static function myFunction() {}
    }
    ```

## 13. Constructor Property Promotion

When using constructor property promotion, [visibility](https://www.php.net/manual/en/language.oop5.visibility.php) must be declared on all properties.

    ```php
    class Point {
        public function __construct(
            private float $x = 0.0,
            private float $y = 0.0,
            private float $z = 0.0,
        ) {}
    }
    ```

## 14. Property Types

Property types, introduced in PHP 7.4, should be added where possible. The colon and type declaration must not have any spaces between them.

    ```php
    class MyClass {
        private int $myProperty;
    }
    ```

## 15. Control Structure Braces

Opening braces for control structures must go on the same line, and the closing brace must go on the next line after the body.

    ```php
    if ($a === $b) {
        echo 'A equals B';
    }
    ```

## 16. Control Structure Else and ElseIf

The else and elseif keywords must be on the same line as the closing brace from the earlier body.

    ```php
    if ($a === $b) {
        echo 'A equals B';
    } else {
        echo 'A does not equal B';
    }
    ```

## 17. Switch Case

The case statement must be indented once from switch. The break keyword (or other terminating keyword) must be indented at the same level as the case body.

    ```php
    switch ($expr) {
        case 0:
            echo 'First case';
            break;
        case 1:
            echo 'Second case';
            break;
        default:
            echo 'Default case';
    }
    ```

## 18. Method and Function Arguments

In the argument list, there must be a space after each comma, and there must be one space on either side of the equals sign used for default value assignments.

    ```php
    function sum($a, $b = 0) {
        return $a + $b;
    }
    ```

## 19. Abstract, Final, and Static

When present, the [abstract](https://www.php.net/manual/en/language.oop5.abstract.php) and [final](https://www.php.net/manual/en/language.oop5.final.php) declarations must precede the visibility declaration. When present, the static declaration must follow the visibility declaration.

    ```php
    abstract class AbstractClass {
        abstract protected function myFunction();
    }

    final class FinalClass {}

    class MyClass {
        public static function myFunction() {}
    }
    ```

## 20. Use Statements

There should be one blank line after the [namespace](https://www.php.net/manual/en/language.namespaces.php) declaration, and one blank line after the [use](https://www.php.net/manual/en/language.namespaces.importing.php) block. Use statements should be alphabetically sorted and grouped.

    ```php
    namespace MyNamespace;

    use My\OtherNamespace\MyClass;
    use My\OtherNamespace\MyOtherClass;

    // Rest of the code
    ```

## 21. Return Type Declarations

The colon and type declaration must not have any spaces between them. There must be one space between the nullable operator and the type, and there must be one space between the closing parenthesis and the colon.

    ```php
    function sum($a, $b): int {
        return $a + $b;
    }
    ```

## 22. If, Elseif, Else

There should be one space on either side of an equals sign used to assign the return value of a function to a variable.

    ```php
    $result = sum($a, $b);
    if ($result === 0) {
        echo 'Result is zero';
    } elseif ($result > 0) {
        echo 'Result is positive';
    } else {
        echo 'Result is negative';
    }
    ```

## 23. For Loops

There should be one space on either side of the initial assignment, condition check, and increment elements of the for control structure.

    ```php
    for ($i = 0; $i < 10; $i++) {
        echo $i;
    }
    ```

## 24. ForEach Loops

For foreach loops that include a key, there should be no space around the arrow.

    ```php
    foreach ($array as $key => $value) {
        echo $key . ': ' . $value;
    }
    ```

## 25. Try, Catch

There should be one space on either side of the vertical bar.

    ```php
    try {
        // Some code
    } catch (FirstExceptionType | SecondExceptionType $e) {
        // Handle exception
    }
    ```

## 26. Closures

Closures must be declared with a space after the function keyword, and a space before and after the use keyword.

    ```php
    $closureWithArgs = function ($arg1, $arg2) use ($var1, $var2) {
        // Some code
    };
    ```

## 27. Closure Return Type

Closures may include a return type, following the same rules as normal functions.

    ```php
    $closureWithArgsAndReturnType = function ($arg1, $arg2) use ($var1, $var2): bool {
        // Some code
        return true;
    };
    ```

## 28. Anonymous Classes

Anonymous Classes should have the same opening brace placement as regular classes and methods.

    ```php
    $instance = new class($constructorArgs) {
        public function myFunction()
        {
            // Some code
        }
    };
    ```

## 29. Multiline Arguments and Array Elements

When splitting function arguments, method arguments, or array elements across multiple lines, there should be one argument or element per line.

    ```php
    $array = [
        'element1',
        'element2',
        'element3',
    ];
    ```

## 30. Commenting

Use `//` for single line comments. Use `/* */` for multi-line comments. Use `/** */` for [PHPDoc](https://docs.phpdoc.org/3.0/guide/getting-started/what-is-a-docblock.html#what-is-a-docblock).

    ```php
    // This is a single line comment

    /*
    This is a
    multi-line comment
    */

    /**
    * This is a PHPDoc comment
    * @var string
    */
    ```

## Conclusion

These are just examples following PHP coding standards. It is important to understand these standards and consistently apply them to your entire codebase. Consistency in code makes it easier to read and maintain.
