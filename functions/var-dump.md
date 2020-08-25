# Var Dump

Insert into functions.php to add formatted var dump and print r actions.

- [Var Dump](#var-dump)
- [Print r](#print-r)

## Var Dump 
```
/**
 * var_dump a value.
 *
 * @param  mixed  $expression
 */
function vardump($expression)
{
    echo '<pre>';
    var_dump($expression);
    echo '</pre>';
}
function vd()
{
    return call_user_func_array('vardump', func_get_args());
}
```
## Print r
```
/**
 * print_r a value.
 *
 * @param  mixed  $expression
 */
function printr($expression)
{
    echo '<pre>';
    print_r($expression);
    echo '</pre>';
}
function pr()
{
    return call_user_func_array('printr', func_get_args());
}
```