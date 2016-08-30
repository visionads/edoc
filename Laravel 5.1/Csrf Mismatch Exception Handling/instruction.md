/**
 * Created by PhpStorm.
 * User: selim
 * Date: 8/30/16
 * Time: 12:07 PM
 */

Token Mismatched in Laravel 5.1
===============================

Step 1 : use {!! csrf_field() !!} in the form.

Step 2: Token MismatchException

        -> in the file “App/Exceptions/Handler.php”
        A). Use Illuminate\Session\TokenMismatchException
        B). And in the method::

        public function render($request, Exception $e)
        {
            if ($e instanceof TokenMismatchException){
                return redirect($request->fullUrl())->with('csrf_error',"Opps! Seems you couldn't submit form for a longtime. Please try again");
            }
            return parent::render($request, $e);
        }


Step 3: Use this code in the App\Http\Middleware\VerifyCsrfToken.php

        Place the all code : http://pastebin.com/P1CnRR57