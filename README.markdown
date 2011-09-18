# nginx Rewrites

- Version: 1.0
- Date: September 18th, 2011
- Github Repository: <http://github.com/bjornpost/nginx_config_templates>

## Overview

This project contains a set of nginx configuration templates which simplify the creation of virtual hosts. The templates in the repository are considered stable, and are tested.

## Templates
- server.error.conf: custom error HTML templates
- server.favicon.conf: serve the favicon.ico. If none is found, serve an empty gif.
- server.gzip.conf: Gzip compression settings for css/js/xml/json/rss files.
- server.listen-local-only: shortcut for listen 8080. Comes in handy if you're using Varnish.
- server.location.deny.conf: Restricts access to .git, .hg, .ht* files and directories.
- server.logging.conf: Set logging for a virtual host.
- server.php5.conf: Enable PHP5 for host.
- server.rewrites.cakephp.conf: Rewrites for CakePHP projects.
- server.rewrites.django.conf: Rewrites for Django projects.
- server.rewrites.symphony2.conf: Rewrites for Symphony 2 projects.
- server.rewrites.wordpress.conf: Rewrites for Wordpress projects.

## How to use
I have prepared some virtual hosts as an example in the examples/ directory. You can use this as a starting point for your own virtual hosts. It mostly comes down to including the right template:

	server {
		server_name wordpress.example.com;
		root /home/example-com/htdocs/wordpress;
		index index.php index.html;

		include templates/server.rewrites.wordpress.conf;
		include templates/server.listen-local-only.conf;
		include templates/server.php5.conf;
		include templates/server.gzip.conf;
		include error.conf;
	}
