# WordPress Coding Standard

## Overview

WordPress has its own coding standards and best practices that developers are encouraged to follow. These coding standards include rules for PHP, HTML, CSS, and JavaScript, and are intended to ensure that all code written for WordPress is consistent and easy to understand.

Here are 50 coding standards with examples for working in WordPress:

## 1. PHP Tag

Always use full PHP tags in WordPress

    ```php
    <?php
    echo 'Hello, WordPress!';
    ?>
    ```

## 2. Indentation

Code should be indented with tabs, not spaces

    ```php
    if ( is_single() ) {
    	the_post();
    	the_content();
    }
    ```

## 3. Space Usage

Put spaces on both sides of the opening and closing parentheses of if, elseif, foreach, array, and switch blocks

    ```php
    if ( $a === $b ) {
    	// Some code
    }
    ```

## 4. Yoda Conditions

When doing logical comparisons, always put the variable on the right side and constants or fixed values on the left

    ```php
    if ( true === $the_force ) {
    	// Do something
    }
    ```

## 5. Single and Double Quotes

When defining an array, wrap the keys in single quotes

    ```php
    $args = array( 'orderby' => 'name', 'order' => 'ASC' );
    ```

## 6. Naming Conventions

Function names should be lowercase and words separated by underscores. They should also be unique so they don't conflict with functions from plugins and WordPress core

    ```php
    function my_custom_function() {
    	// Some code
    }
    ```

## 7. Prefixing

All function names, classes, hooks, public global variables, and database entries should be prefixed with a unique identifier to avoid collisions with plugins and themes

    ```php
    function myplugin_custom_function() {
    	// Some code
    }
    ```

## 8. Database Queries

Always use the [$wpdb](https://developer.wordpress.org/reference/classes/wpdb/) class for database queries

    ```php
    global $wpdb;
    $wpdb->get_results( "SELECT * FROM $wpdb->posts WHERE post_status = 'publish'" );
    ```

## 9. Nonces

Use [nonces](https://developer.wordpress.org/apis/security/nonces/) to verify intent of the user's action

    ```php
    wp_nonce_field( 'myplugin_nonce_action', 'myplugin_nonce_field' );
    ```

## 10. Checking User Permissions

Always use [current_user_can()](https://developer.wordpress.org/reference/functions/current_user_can/) before performing a capability sensitive operation

    ```php
    if ( current_user_can( 'manage_options' ) ) {
    	// Do something
    }
    ```

## 11. Localization

Make all text output translatable using [__()](https://developer.wordpress.org/reference/functions/__/), [_e()](https://developer.wordpress.org/reference/functions/_e/), [_n()](https://developer.wordpress.org/reference/functions/_n/), [_x()](https://developer.wordpress.org/reference/functions/_x/), [_ex()](https://developer.wordpress.org/reference/functions/_ex/), [_nx()](https://developer.wordpress.org/reference/functions/_nx/) functions

    ```php
    _e( 'Hello, World!', 'my-plugin' );
    ```

## 12. Closing PHP tags

Omit closing PHP tags if the file only contains PHP code

    ```php
    // Correct
    <?php
    echo 'Hello, WordPress!';
    ```

## 13. WordPress Functions

Always use WordPress functions when possible instead of PHP built-in functions. For example, use [wp_safe_redirect()](https://developer.wordpress.org/reference/functions/wp_safe_redirect/) instead of header()

    ```php
    wp_safe_redirect( $location, $status );
    ```

## 14. Sanitization

Always sanitize untrusted data before use in a SQL query to prevent potential security issues

    ```php
    $id = sanitize_key( $_GET['id'] );
    ```

## 15. Escaping

Escape all untrusted data before output

    ```php
    echo '<a href="' . esc_url( $url ) . '">' . esc_html( $text ) . '</a>';
    ```

## 16. Error Reporting

Turn WP_DEBUG to true in your wp-config.php file while developing

    ```php
    define( 'WP_DEBUG', true );
    ```

## 17. No Shorthand PHP tags

Never use shorthand PHP start tags

    ```php
    <?php echo 'Hello, WordPress!'; ?>
    ```

## 18. Including Files

Use [get_template_directory()](https://developer.wordpress.org/reference/functions/get_template_directory/) instead of TEMPLATEPATH for include files

    ```php
    include( get_template_directory() . '/myinclude.php' );
    ```

## 19. Including Templates

Use [get_template_part()](https://developer.wordpress.org/reference/functions/get_template_part/) for including template parts

    ```php
    get_template_part( 'content', get_post_format() );
    ```

## 20. Conditional Tags

Use WordPress specific conditional tags when possible

    ```php
    if ( is_single() ) {
    	// Do something
    }
    ```

## 21. Plugin and Theme Data

Use [get_option()](https://developer.wordpress.org/reference/functions/get_option/) to retrieve plugin data stored in the database

    ```php
    $options = get_option( 'myplugin_options' );
    ```

## 22. Data Validation

Validate and sanitize user input

    ```php
    $username = sanitize_user( $_POST['username'] );
    ```

## 23. Echoing vs Returning

When creating a function, decide if it needs to echo or return and make sure it does only one of these things

    ```php
    function myplugin_return_content() {
    	$content = 'Hello, WordPress!';
    	return $content;
    }
    ```

## 24. Multiline Array Syntax

Use multiline array syntax for long arrays

    ```php
    $array = array(
    	'key1' => 'value1',
    	'key2' => 'value2',
    	'key3' => 'value3',
    );
    ```

## 25. Self-Closing Tags

Use self-closing tags for input, img and hr

    ```php
    <input type="text" name="firstname" id="firstname" />
    ```

## 26. HTML Quotes

Always use double quotes for HTML and XML tags

    ```php
    <div class="container"></div>
    ```

## 27. Inline Documentation

Use [DocBlocks](https://docs.phpdoc.org/guide/getting-started/what-is-a-docblock.html#what-is-a-docblock) to document functions, classes, methods, and hooks

    ```php
    /**
     * My custom function.
     *
     * @param string $param My parameter.
     */
    function my_custom_function( $param ) {
    	// Some code
    }
    ```

## 28. Action and Filter Hooks

Prefix your custom hooks with your theme or plugin prefix

    ```php
    do_action( 'myplugin_custom_hook' );
    ```

## 29. Global Variables

Global variables should be used sparingly

    ```php
    global $post;
    the_title();
    ```

## 30. Enqueue Scripts and Styles

Always use [wp_enqueue_script()](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) and [wp_enqueue_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) to include JavaScript and CSS files

    ```php
    wp_enqueue_script( 'myplugin-script', plugins_url( '/js/script.js', __FILE__ ), array( 'jquery' ) );
    ```

## 31. Inline Control Structures

No inline control structures; always use full (curly-brace) syntax in conditional statements and loops

    ```php
    if ( is_single() ) {
        the_post();
    } else {
        echo 'Not a single post';
    }
    ```

## 32. Constants

Define constants in uppercase with underscores

    ```php
    define( 'MYPLUGIN_VERSION', '1.0.0' );
    ```

## 33. Database Prefix

Always use the $wpdb->prefix when referencing any core WordPress table

    ```php
    global $wpdb;
    $wpdb->get_results( "SELECT * FROM {$wpdb->prefix}options" );
    ```

## 34. Strict Comparisons

Always use strict comparisons if possible

    ```php
    if ( $foo === $bar ) {
        // Some code
    }
    ```

## 35. Form Processing

Always process form data in the `admin_post_{action}` or `admin_post_nopriv_{action}` hooks

    ```php
    function myplugin_form_process() {
        // Form processing code here
    }
    add_action( 'admin_post_my_form', 'myplugin_form_process' );
    ```

## 36. Shortcodes

Create shortcodes for custom functionality that needs to be displayed in posts or pages

    ```php
    function myplugin_custom_shortcode( $atts ) {
        // Shortcode functionality here
    }
    add_shortcode( 'myshortcode', 'myplugin_custom_shortcode' );
    ```

## 37. Widgets

For custom widgets, extend the [WP_Widget](https://developer.wordpress.org/reference/classes/wp_widget/) class

    ```php
    class MyPlugin_Widget extends WP_Widget {
        // Widget code here
    }
    add_action( 'widgets_init', function(){
        register_widget( 'MyPlugin_Widget' );
    });
    ```

## 38. Template Tags

Use WordPress [template tags](https://developer.wordpress.org/themes/basics/template-tags/) whenever possible

    ```php
    the_content();
    ```

## 39. User Meta

Use [get_user_meta()](https://developer.wordpress.org/reference/functions/get_user_meta/) and [update_user_meta()](https://developer.wordpress.org/reference/functions/update_user_meta/) to get and update user metadata

    ```php
    $user_id = get_current_user_id();
    $meta_value = get_user_meta( $user_id, 'my_meta_key', true );
    ```

## 40. Post Meta

Use [get_post_meta()](https://developer.wordpress.org/reference/functions/get_post_meta/) and [update_post_meta()](https://developer.wordpress.org/reference/functions/update_post_meta/) to get and update post metadata

    ```php
    $post_id = get_the_ID();
    $meta_value = get_post_meta( $post_id, 'my_meta_key', true );
    ```

## 41. Deprecated Functions

Do not use deprecated functions. If you have to use a function that is deprecated, make sure it is wrapped in a conditional that checks the WP version

    ```php
    if ( version_compare( $GLOBALS['wp_version'], '5.0', '<' ) ) {
        // Use old function
    }
    ```

## 42. Error Handling

Always check the return types of functions and handle errors appropriately

    ```php
    $post_id = wp_insert_post( $post_data );
    if ( is_wp_error( $post_id ) ) {
        // Handle error
    }
    ```

## 43. Default Break in Switch

Always have a default case in switch blocks

    ```php
    switch ( $var ) {
        case 'value':
            // Do something
            break;
        default:
            // Default case
            break;
    }
    ```

## 44. Enqueue in Hook

Always enqueue scripts and styles in the appropriate hook

    ```php
    function myplugin_enqueue_scripts() {
        wp_enqueue_script( 'myplugin-script', plugins_url( '/js/script.js', __FILE__ ), array( 'jquery' ) );
    }
    add_action( 'wp_enqueue_scripts', 'myplugin_enqueue_scripts' );
    ```

## 45. Use WordPress Constants

Use WordPress constants for file paths and URLs

    ```php
    require_once( ABSPATH . 'wp-settings.php' );
    ```

## 46. Avoid Direct Database Queries

Use WordPress functions like [get_posts()](https://developer.wordpress.org/reference/functions/get_posts/) or [WP_Query](https://developer.wordpress.org/reference/classes/wp_query/) instead of direct database queries when possible

    ```php
    $args = array( 'posts_per_page' => 5 );
    $recent_posts = get_posts( $args );
    ```

## 47. Follow WordPress File Structure

When building themes, follow the WordPress file structure conventions.

## 48. Use the Customizer for Theme Options

Do not create theme options pages. Use the Customizer API instead.

## 49. Security Nonces in Forms

Always include a nonce field in forms for verification.

    ```php
    wp_nonce_field( 'myplugin_form_action' );
    ```

## 50. Post Status Transitions

Use the [transition_post_status](https://developer.wordpress.org/reference/hooks/transition_post_status/) hook to perform actions when a post's status changes.

    ```php
    function myplugin_on_publish( $new_status, $old_status, $post ) {
        if ( 'publish' === $new_status && 'publish' !== $old_status ) {
            // A post was just published
        }
    }
    add_action( 'transition_post_status', 'myplugin_on_publish', 10, 3 );
    ```

## Conclusion

These examples should provide a solid understanding of WordPress coding standards and best practices. Following these rules will help you write clear, consistent, and secure code that is compatible with the rest of the WordPress ecosystem.
