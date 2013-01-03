## Hijri Bundle

The Laravel Hijri bundle can be used to convert Gregorian dates to Islamic Hijri


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

## Usage/Examples


#### Hijri date for Todays date

```php
Timer::start('name-of-timer');

// will return  الجمعة, 08 ربيع الأول 1432 06:10 صباحاً
```

#### Creating multiple timers
You can create as many unique timers as you'd like.

```php
Timer::start('first-timer');
Timer::start('second-timer');
```

#### Adding checkpoints to an existing timer

Checkpoints can be created for an existing timer which will calculate the time from start as well as the time since last checkpoint.
If you are familiar with the built in profiler and ticks, checkpoints are essentially the same thing. They are useful if you wish to
use a single timer throughout your application and add in your own breakpoints.

```php
Timer::start('my-timer-name');

// do some work
sleep(2);

// create a checkpoint
Timer::checkpoint('my-timer-name', 'The first checkpoint after sleeping 2 seconds.');

// do some more work
sleep(1);

// another checkpoint
Timer::checkpoint('my-timer-name', 'A second checkpoint which will also calculate time elapsed from first checkpoint.');

// some other stuff
sleep(3);

// end the timer and use return values as you please
$values = Timer::stop('my-timer-name');
```

#### Retrieving timer results
While you can retrieve a single timer's results as an array by calling `Timer::stop()`,
you can also retrieve the full set of all timer results as a multi-dimensional array
by calling `Timer::dump()`. If you have any currently running timers that you failed
to stop, `Timer::dump()` makes sure to handle stopping them.

`Timer::dump()` also takes a single boolean parameter, `$toFile`, which will create
a timestamped log file in `storage/logs/timer_YYYY-MM-DD_HHiiSS.log`. This is
helpful if you don't want to manually deal with your existing timers and prefer to
analyze the results at a later date. The other benefit of storing timer results in
a log file is that Timer will pretty print your results as JSON for easier readability.

```php
Timer::start('my-timer');

// some work
sleep(1);

// create a second timer for the hell of it
Timer::start('second-timer');

// create a checkpoint on the first timer
Timer::checkpoint('my-timer', 'A checkpoint for no good reason.');

// some more work
sleep(2);

// choose one of the following two (with the second exporting results to log file)
Timer::dump();
Timer::dump(true);
```

#### Resetting all timers
Timer has a built in method to clear out (reset) all pre-existing timers so you
can start fresh. Likewise, simply re-using a timer name in `Timer::start()`
will also clear out and re-initialize a single timer.

```php
// start a timer
Timer::start('my-timer');

// clear all existing timers
Timer::clear();

// we can reuse the existing timer
Timer::start('my-timer');
```

## License

The MIT License (MIT)

Copyright (c) 2012, Craft Blue, LLC

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
