# Remove Empty Folders Recursively

This will delete a path and sub-folders if they are found to be empty. Note the passed directory will be deleted if all sub-directories and itself are empty. 

If the folder contains hidden files, it will _not_ be deleted. Watch out if using MacOS as it has a habit of creating `.DS_Store` files in folders.

Originally borrowed and modified from: [https://stackoverflow.com/a/1833681](https://stackoverflow.com/a/1833681)


```php
/**
 * This will delete a path and sub-folders if they are found to be empty. Note the passed
 * directory will be deleted if all sub-directories and itself are empty.
 *
 * If the folder contains hidden files, it will _not_ be deleted. Watch out if using MacOS
 * as it has a habit of creating .DS_Store files in folders.
 *
 * Originally borrowed and modified from: https://stackoverflow.com/a/1833681
 *
 * @param string $path The initial path to begin the search and remove from.
 * @return bool Whether the folder is empty (true) or not (false).
 */
public static function remove_empty_folders_recursive(string $path): bool
{
    $is_empty = true;

    foreach( glob($path.DIRECTORY_SEPARATOR."*", GLOB_BRACE) as $sub_path )
    {
        if( is_dir($sub_path) ) {
            if( !self::remove_empty_folders_recursive($sub_path) )
                $is_empty = false;
        }
        else {
            $is_empty = false;
        }
    }

    if( $is_empty ) {
        Log::debug('Deleting: ' . $path);
        rmdir( $path );
    }

    return $is_empty;
}
```