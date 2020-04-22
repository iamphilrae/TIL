# Remove Unwanted Files from Folders Recursively

The following function will recursively delete unwanted files from sub-folders of a passed path.

```php
/**
 * Recursively delete unwanted files from a path and its sub-folders.
 *
 * @param string $path The initial path to begin the search and remove from.
 * @param array $unwanted_list Files to remove, e.g. [".DS_Store", ".gitignore"]
 */
public static function remove_unwanted_files_recursive(string $path, array $unwanted_list): void
{
    foreach( glob($path . DIRECTORY_SEPARATOR . "{*,.[!.]*,..?*}", GLOB_BRACE) as $sub_path )
    {
        if( is_dir($sub_path) ) {
            self::remove_unwanted_files_recursive($sub_path, $unwanted_list);
        }
        else if( in_array( basename($sub_path), $unwanted_list ) ) {
            unlink($sub_path);
        }
    }
}
```
