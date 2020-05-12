# Generate Checksum

The following function generate a checksum from a provided string. Good for validating if a long string has changed or not (checksums will match)


```php
/**
 * Generates a hash checksum from a provided string.
 *
 * @param string $str
 * @param string $algorithm
 * @return string The hash checksum
 */
public static function generateChecksum( string $str, string $algorithm='sha1' ): string
{
    return hash( $algorithm, $str );
}
```