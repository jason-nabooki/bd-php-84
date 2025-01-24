## About

Repository that replicates the issue reported in [this issue](https://github.com/hisorange/browser-detect/issues/227).

This issue only seems replicable when a route with Route Model Bindings is requested more than once and the route handler is using the Browser Detect package.

See `ProfileController.php@show`

**Steps to replicate**

1. Clone the repository
2. Ensure your PHP version is `8.4`
3. Run `composer install`
4. Run `npm install`
5. Run `php artisan key:generate`
6. Run `php artisan migrate`
7. Run `npm build`
8. Run `php artisan test`

Note: The test `test_profile_page_is_displayed_for_specific_user` will fail with the error `zend_mm_heap corrupted`

**Repository details**

This is a fresh Laravel 11 project with the Laravel Breeze starter kid (Blade and Alpine).

The Browser Detect package was installed.

A route with Route Model Binding was added (`profile.show` see `routes/web.php`) and a handler `ProfileController.php@show`.

When this route is requested more than once, the `zend_mm_heap corrupted` error is thrown as seen by the `test_profile_page_is_displayed_for_specific_user` test.