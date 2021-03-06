#Yothalot\Output

Yothalot\Output is a utility class that helps you to create files in the same 
[format](copernica-docs:Yothalot/internalfiles "Internal Files") as Yothalot 
uses internally. In general you do not need to create a file like this since
Yothalot can handle all types of files (with a little bit of your help). However, the 
Yothalot format has the cool property of being compressed while still being
splittable. Therefore you may want to use this format for your own files as well.

There are five methods available for this class:
```php
class Yothalot\Output
{
    public function __construct($filename);
    public function add($identifier, $fields);
    public function name();
    public function size();
    public function flush();
}
```
## Constructor
The constructor takes one parameter, the file name. A file with this 
file name will be created if it does not exist. Otherwise the file will 
be opened. 

```php
/**
 * Create or open an output file
 */
$output = new Yothalot\Output("/path/to/file.log");
```
where `"/path/to/file.log"` is the path to the file you want to write to.

## Member add()
add() is a member that adds a record to the output file. A record exists
of an identifier and fields. The identifier has to be numeric. The field
can be an array of basic types.
```php
/**
 * Add a record with key and value to output file
 */
$output->add(1, array('1', '2', '3'));
```
where: `1` is in this case the identifier and `array('1', '2', '3')` are
the fields.


## Member name()
name() returns the full name of the output file.
```php
/**
 * Get the name of the output file
 */
echo($output->name());
```

##Member size()
Yothalot::Output::size() returns the size (in bytes) of the output file. You
may use it e.g. to determine if the file has become to large, so
you can close it and create a new output file. However, note that
the Yothalot formated files are splittable.
```php
/**
 * Retrieve the size of the output file
 */
echo($output->size());
```

##Member flush()
Yothalot::Output::flush() flushes the object to the file. In general
you do not need this, only if your code can crash you may use it to be
sure that your data is stored. Although it is better to fix the code.
```php
/**
 * flush the data to the output file
 */
$output->flush();
```
