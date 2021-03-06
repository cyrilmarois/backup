## Backup

Backup is a Laravel package that allow the creation and restoration of database backups in an easy way.

> For Laravel 5.1 see [5.1 branch](https://github.com/paulvl/backup/tree/5.1)

[![Latest Stable Version](https://poser.pugx.org/paulvl/backup/v/stable)](https://packagist.org/packages/paulvl/backup)  [![Latest Unstable Version](https://poser.pugx.org/paulvl/backup/v/unstable)](https://packagist.org/packages/paulvl/backup) [![License](https://poser.pugx.org/paulvl/backup/license)](https://packagist.org/packages/paulvl/backup) [![Total Downloads](https://poser.pugx.org/paulvl/backup/downloads)](https://packagist.org/packages/paulvl/backup)

## **Quick Installation**

Begin by installing this package through Composer.

You can run:

    composer require paulvl/backup 2.*

Or edit your project's composer.json file to require paulvl/backup.
```
    "require": {
        "paulvl/backup": "2.*"
    }
```
Next, update Composer from the Terminal:

    composer update

Once the package's installation completes, the final step is to add the service provider. Open `config/app.php`, and add a new item to the providers array:

```
Backup\BackupServiceProvider::class,
```

Finally publish package's configuration file:

    php artisan vendor:publish --provider="Backup\BackupServiceProvider"

Then the file `config/backup.php` will be created.

That's it! You're all set to go. Run the artisan command from the Terminal to see the new `backup` commands.

    php artisan

## **Mysql**

### **Creating a backup**
To make a backup of you current aplicationa database you have to run:

    php artisan backup:mysql-dump

This will create an `.sql` file on your configured path like `/this/is/my/path/dbname_20150101201505.sql`, this file is named using current datetime. If you want a custom name run:

    php artisan backup:mysql-dump example

This will create an `.sql` file on your configured path like `/this/is/my/path/example.sql`

### **Restoring database from file**
To restore a backup to your current aplication in a database you have to run:

    php artisan mysql:restore filename

This will restore the `/this/is/my/path/filename.sql` file stored on your configured.

### **Programing backups**
If you need to perform a backup for example, every day at midnight, at this like to yor schedule function on `app/Console/Commands/Kernel.php`:
```
protected function schedule(Schedule $schedule)
{
...
    $schedule->command('backup:mysql-dump')->dailyAt('00:00');
...
}
```
## **Contribute and share ;-)**
If you like this little piece of code share it with you friends and feel free to contribute with any improvements.


