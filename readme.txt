=== Zend AMF Interfaces ===
Contributors: 99bots
Tags: zend, adobe, amf, action, message, format, protocol, php5
Tested up to: 2.9.2
Requires at least: 2.0
Stable tag: 1.10.6
Donate link: http://99bots.com/donate

The Zend AMF interfaces contain everything you need for using Adobe's Action Message Format protocol in order to run Adobe Flex and Adobe AIR applications from your PHP 5 Wordpress installation.

== Description ==

This plugin embeds and loads the Zend AMF PHP 5 client interfaces for Adobe's Action Message Format protocol (for building Adobe Flex and Adobe AIR applications) so that the client interfaces can be shared by different Wordpress plugins.    

This plugin fulfills the Zend AMF Framework dependency for other Wordpress plugins.  A significant benefit of using this plugin as your Zend AMF dependency instead of including the Zend AMF Framework directly in your individual plugins is to minimize redundancy, and to guarantee the latest version of the Zend AMF Framework.

The Zend AMF Framework is an open source, object-oriented web application framework implemented in PHP 5 and licensed under the New BSD License.

The current version uses Zend AMF 1.10.6

== Installation ==

1. Upload `plugin-name.php` to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress

See "Other Notes" for usage.

== Usage ==

Zend AMF Interfaces is automatically made available in the PHP include path.

You may check Zend AMF Interfaces availability using the WP_ZEND_AMF_INTERFACES constant.  Here is an example of how to do that in your plugin code:

`function check_for_zend_amf_interfaces() {
  // if the Zend AMF Interfaces plugin is successfully
  // loaded this constant is set to true
  if (defined('WP_ZEND_AMF_INTERFACES') && 
     constant('WP_ZEND_AMF_INTERFACES')) {
    return true;
  }
  // you can also check if the Zend AMF Interfaces are 
  // available on the system
  $paths = explode(PATH_SEPARATOR, get_include_path());
  foreach ($paths as $path) {
    if (file_exists("$path/Zend/Loader.php")) {
      define('WP_ZEND_AMF_INTERFACES', true);
      return true;
    }
  }
  // nothing found, you may advice the user to install 
  // the Zend AMF Interfaces plugin
  define('WP_ZEND_AMF_INTERFACES', false);
}

add_action('init', 'check_for_zend_amf_interfaces');`
