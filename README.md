## Hijri Bundle

The Laravel Hijri bundle can be used to convert Gregorian to formatted Islamic Hijri date.

## Installing using Artisan CLI:

```bash
php artisan bundle:install hijri
```

Either auto-load the bundle in application/bundles.php:

```php
return array(
    'hijri' => array('auto' => true)
);
```

Or manually start:

```php
Bundle::start('hijri');
```

#### To get the Arabic translation for Hijri date
Set the "language" in application\config\application.php to "ar"

```php
	/*
	|--------------------------------------------------------------------------
	| Default Application Language
	|--------------------------------------------------------------------------
	|
	| The default language of your application. This language will be used by
	| Lang library as the default language when doing string localization.
	|
	*/

	'language' => 'en',

```

## Usage/Examples


#### Hijri date for Todays date

```php
Hijri::date("H:i A l, d F Y",time());

// will return  الجمعة, 08 ربيع الأول 1432 06:10 صباحاً
```

#### Getting Hijri date from String date

```php
Hijri::HijriToString("19 June 2012");
// it will return 29-7-1433
```

#### Or with specific date format

You need to use PHP date() "format character" see http://php.net/manual/en/function.date.php.

```php
Hijri::HijriToString("19 June 2012", "l, d-F-Y");
// it will return formatted date string in Hijri الثلاثاء, 29-رجب-1433

```

## License

The MIT License (MIT)

Copyright (c) 2012, Abdulrhman Alkhodiry

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
