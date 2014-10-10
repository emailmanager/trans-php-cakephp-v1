Emailmanager CakePHP component
==========================

Copyright 2010, Daniel McOrmond
Licensed under The MIT License
Redistributions of files must retain the above copyright notice.


Version
-------

Written for CakePHP 1.3+


Configuration
-------------

Add the following keys to your configuration:

	Configure::write('Emailmanager.uri', 'http://trans.emailmanager.com/email');
	Configure::write('Emailmanager.key', '810de23c-5ffb-44d9-a424-7a4a5c0fba1a');

If you want your connection to Emailmanager to be encrypted, simply change the uri to use https.

Make sure to modified the API key to match the credentials for your Emailmanager server rack instance.


Usage
-----

This component extends the base CakePHP email component, and works virtually the same.

Place the emailmanager.php file in your app/controllers/components/ folder.

In your controller, make sure the component is available:

	public $components = array('Emailmanager');   

Then, simply send messages like this:

	$this->Emailmanager->delivery = 'emailmanager';
	$this->Emailmanager->from = '<sender@domain.com>';
	$this->Emailmanager->to = '<recipient@domain.com>';
	$this->Emailmanager->subject = 'this is the subject';
	$messageBody = 'this is the message body';
	$this->Emailmanager->send($messageBody);

You can also use the following optional attributes:

	$this->Emailmanager->cc = '<recipient@domain.com>';
	$this->Emailmanager->bcc = '<recipient@domain.com>';
	$this->Emailmanager->replyTo = '<sender@domain.com>';

To send to multiple recipients, simply use an array of addresses in the 'to', 'cc', or 'bcc' fields. For example:

	$this->Emailmanager->cc = array('<recipient@domain.com>', '<another@domain.com>');

The syntax of all parameters is the same as the default CakePHP email component:

	http://book.cakephp.org/view/1283/Email

There is one additional attribute which can be used for setting the Emailmanager tag property:

	$this->Emailmanager->tag = 'contact';

For more information, see the Emailmanager API documentation:

	http://trans.emailmanager.com/#message-format


Debugging
--------

You can see the response from Emailmanager in the return value when you send a message:

	$result = $this->Emailmanager->send($messageBody);
	$this->log($result, 'debug');

If there are any errors, they'll be included in the response. See the Emailmanager API documentation for error code detail:

	http://trans.emailmanager.com/#api-error-codes
