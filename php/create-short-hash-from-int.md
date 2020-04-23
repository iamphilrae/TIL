# Create Short Hash from Int

This function creates a short lowercase hash from an integer, e.g. `1234` returns `ax`. Can be useful for creating non-encrypted (non-sensitive) strings for things like folder names from ID numbers.

```php
/**
 * Creates a short lowercase hash from an integer. E.g. `1234` returns `ax`
 * @param int $val
 * @return string
 */
public static function short_hash( int $val ): string {
    return base_convert($val, 10, 36);
}
```