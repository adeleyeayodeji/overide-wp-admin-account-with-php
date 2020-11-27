# WordPress Admin Overide Auth
As a developer, you will occasionally need to create a new administrative user in the database to gain access to the site. Typically, this is necessary when you are provided with an export of a WordPress database, but you aren’t provided with the login credentials for the admin user.

Sure, you can gain access via the database. However, many developers aren’t very comfortable with MySQL and the process is pretty slow compared to what I’m about to show you. Here’s all you need to do:

  - Create an mu-plugins/ directory in your site’s wp-content/ directory.
  - Create a new file in the wp-content/mu-plugins/ directory you created and name it anything you want. Something like create-admin-user.php would work nicely.
  - Copy this code snippet and paste it into the file you just created:
```php
<?php

add_action( 'init', function () {
  
	$username = 'admin';
	$password = 'password';
	$email_address = 'webmaster@mydomain.com';

	if ( ! username_exists( $username ) ) {
		$user_id = wp_create_user( $username, $password, $email_address );
		$user = new WP_User( $user_id );
		$user->set_role( 'administrator' );
	}
	
} );
```
  - Edit the username, password and email address.
  - Login to the site using the information you just edited.

Once you have logged in, delete the file.




