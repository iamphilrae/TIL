# Validate Integer

The following function will validate whether a value passed, either as a _string_ or an _int_, is an integer.


```php
/**
 * Check if expression is an integer, either a type String or int.
 * 
 * @param string|int $value
 * @return bool
 */
public static function is_integer( $value ): bool
{
    if(gettype($value) == 'integer')
        return true;

    if(gettype($value) == 'string') {
        if (substr($value, 0, 1) == '-') {
            $value = substr($value, 1);
        }
        return (is_int($value) || ctype_digit($value));
    }

    return false;
}
```