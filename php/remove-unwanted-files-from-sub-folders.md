# Remove Unwanted Files from Sub-Folders

The following function will recursively delete unwanted files from sub-folders of a passed path.

```php
/**
 * Recursively delete unwanted files from sub-folders of a passed path.
 *
 * @param string $path The initial path to begin the search and remove from.
 * @param array $unwanted_list Files to remove, e.g. [".DS_Store", ".gitignore"]
 */
public static function remove_unwanted_files_from_sub_folders(string $path, array $unwanted_list): void
{
    foreach( glob($path . DIRECTORY_SEPARATOR . "{*,.[!.]*,..?*}", GLOB_BRACE) as $sub_path )
    {
        if( is_dir($sub_path) ) {
            self::remove_unwanted_files_from_sub_folders( $sub_path, $unwanted_list );
		}
        else if( in_array( basename($sub_path), $unwanted_list ) ) {
            // error_log('Deleting: ' . $sub_path );
            unlink($sub_path);
        }
    }
}
```