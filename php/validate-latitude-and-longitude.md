# Validate Latitude and Longitude

The following functions will validate a value passed as to whether they are valid latitude and longitude degree values.

Valid latitude values are between -90 and +90.

Valid longitude values are between -180 and +180.


## Latitude Validation

```php
/**
 * Validates a given latitude $lat in degrees. Valid values are 
 * between -90 and +90.
 *
 * @param float|int|string $lat Latitude
 * @return bool `true` if $lat is valid, `false` if not
 */
public static function is_valid_latitude($lat)
{
    return preg_match('/^(\+|-)?(?:90(?:(?:\.0{1,6})?)|(?:[0-9]|[1-8][0-9])(?:(?:\.[0-9]{1,6})?))$/', $lat);
}
```

## Longitude Validation

```php
/**
 * Validates a given longitude $long in degrees. Valid values are 
 * between -180 and +180.
 *
 * @param float|int|string $long Longitude
 * @return bool `true` if $long is valid, `false` if not
 */
public static function is_valid_longitude($long)
{
    return preg_match('/^(\+|-)?(?:180(?:(?:\.0{1,6})?)|(?:[0-9]|[1-9][0-9]|1[0-7][0-9])(?:(?:\.[0-9]{1,6})?))$/', $long);
}
```