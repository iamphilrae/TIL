# Validate Positive Integer

The following function will validate whether a value passed, either as a _string_ or an _int_, is a positive integer.


```php
/**
 * Check if expression is positive integer, either a type String or int.
 *
 * @param string|int $value
 * @return bool
 */
public static function is_positive_integer($value): bool
{
    if(gettype($value) == 'integer')
        return true;

    if(gettype($value) == 'string')
        return ((is_int($value) || ctype_digit($value)) && (int)$value > 0);

    return false;
}
```