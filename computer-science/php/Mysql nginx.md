# Mysql nginx

`ssh root@C7y0G3n`
` `
`ksec_cms`
` `
`root@xogCuc-codxyn-gefto6`
`ksec@hoqnak-fefxom-xuKnu1`
`phpmyadmin@gufbe7-joSwip-rokmyx`
` `
`WP`
`koyanloshe@4jbJGU*TTyKOOR7UKl`
` `
` `
`/**#@+`
` * Authentication Unique Keys and Salts.`
` *`
` * Change these to different unique phrases!`
` * You can generate these using the {@link `_`https://api.wordpress.org/secret-key/1.1/salt/`_` WordPress.org secret-key service}`
` * You can change these at any point in time to invalidate all existing cookies. This will force all users to have to log in again.`
` *`
` * @since 2.6.0`
` */`
`/**define('AUTH_KEY',         'put your unique phrase here');`
`define('SECURE_AUTH_KEY',  'put your unique phrase here');`
`define('LOGGED_IN_KEY',    'put your unique phrase here');`
`define('NONCE_KEY',        'put your unique phrase here');`
`define('AUTH_SALT',        'put your unique phrase here');`
`define('SECURE_AUTH_SALT', 'put your unique phrase here');`
`define('LOGGED_IN_SALT',   'put your unique phrase here');`
`define('NONCE_SALT',       'put your unique phrase here');`
`**/`
`define('AUTH_KEY',         'NIaa~gSV~e[st^#&iu.%er6`mh(lryX-Alt?HSoKKB.tav;t-]}j+hxXWzv ,5|4');`
`define('SECURE_AUTH_KEY',  '/GYb`-s0|^Hg^G?}}9DGs;n80[QE0KF[-P.5|JXMjP#iokK!+f=+I[`5vJh`NIyx');`
`define('LOGGED_IN_KEY',    '<?=$TD`126d_x)cWZ*Qx|FA|5yKA`3Tn[K~]GIR/30h^[42b8H0|r5ZK_@X=f81i');`
`define('NONCE_KEY',        '+r,$b-$q3]>n[,{+5cepHQ7TXTXIo&c-X|ZA-J%M.*n%)A&JZ8!Rnl`ll^krPTuL');`
`define('AUTH_SALT',        '&7cr1^n9wm C%jQ.W~)a}lW2Z=BSU5v6SC( 6-nC, ~RD1aRhu{498ByA|D/dxAv');`
`define('SECURE_AUTH_SALT', 'K$|m+XO>ivkm8]cFz9v#GBk=nANvwzS3^uu!r0 _7pZ+(5+=-2b4q>7o=a5^/?o7');`
`define('LOGGED_IN_SALT',   'HM(;v:Yk`IS8.&5x5,brl#r>mw5Z+p:)1 I8{7o:Jd9x]D {31#_,aJ6 0_)7cV=');`
`define('NONCE_SALT',       'o|}8mQt0?9I2^_<x`Of,Sf&7Zi)/,p}o~)v2N-_qva4-|=V}MM:Ri&Q9wz%<+$)$');s`
` `
`/**#@-*/`
` `
`/**`
` * WordPress Database Table prefix.`
` *`
` * You can have multiple installations in one database if you give each`
` * a unique prefix. Only numbers, letters, and underscores please!`
` */`
`$table_prefix  = 'wp_';`
` `
`/**`
` * For developers: WordPress debugging mode.`
` *`
` * Change this to true to enable the display of notices during development.`
` * It is strongly recommended that plugin and theme developers use WP_DEBUG`
` * in their development environments.`
` *`
` * For information on other constants that can be used for debugging,`
` * visit the Codex.`
` *`
` * @link `_`https://codex.wordpress.org/Debugging_in_WordPress`_

` */`
`define('WP_DEBUG', true);`
` `
`/* That's all, stop editing! Happy blogging. */`
` `
`/** Absolute path to the WordPress directory. */`
`if ( !defined('ABSPATH') )`
`        define('ABSPATH', dirname(__FILE__) . '/');`
` `
`/** Sets up WordPress vars and included files. */`
`require_once(ABSPATH . 'wp-settings.php');`

