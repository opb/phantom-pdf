Phantom PDF
===========

A Package for generating PDF files using PhantomJS. The package is framework agnostic, but provides integration with Laravel 4.

Notice: This package only works on 64-bit Linux operating systems.

##Installation
Add `danielboendergaard/phantom-pdf` to your `composer.json` file.

````
"require": {
  "danielboendergaard/phantom-pdf": "0.*"
}
````

Then run `composer update`

####Laravel Installation (optional)

Add the service provider in the `providers` array in `app/config/app.php`
````
'providers' => [
  ...
  'PhantomPdf\Laravel\PhantomPdfServiceProvider'
]
````

Lastly, add the facade to the `aliases` array in `app/config/app.php` (optional)
````
'aliases' => [
  ...
  'PDF' => 'PhantomPdf\Laravel\PDFFacade'
]
````

##Usage with Laravel
````php
class SampleController extends Controller {

  public function index()
  {
    $view = View::make('index');
    
    return PDF::createFromView($view, 'filename.pdf');
  }
}
````

##Usage outside Laravel

````php

$generator = new PdfGenerator;

$generator->setStoragePath('storage/path');

// Returns a Symfony\Component\HttpFoundation\BinaryFileResponse
return $generator->createFromView($html, 'filename.pdf');

````
