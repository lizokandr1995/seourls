# phpBB SEO URLs for non-latin languages

* `/viewforum.php?f=1 becomes /forum/1/`
* `/viewtopic.php?f=1&t=2 becomes /forum/1/topic/2/`
* `/viewtopic.php?f=1&t=2&start=3 becomes /forum/1/topic/2/start/3/`
* `/viewtopic.php?p=1 becomes /post/1/`

nginx config rules. add these to location / {
	
rewrite ^/forum/([0-9]*)/mcp\.php(.*) mcp.php?$query_string last;

rewrite ^/forum/([0-9]*)/topic/([0-9]*)/start/([0-9]*) /viewtopic.php?f=$1&t=$2&start=$3&$query_string last;

rewrite ^/forum/([0-9]*)/topic/([0-9]*)/start/([0-9]*)/ /viewtopic.php?f=$1&t=$2&start=$3&$query_string last;

rewrite ^/forum/([0-9]*)/topic/([0-9]*)/ /viewtopic.php?f=$1&t=$2&$query_string last;

rewrite ^/forum/([0-9]*)/topic/([0-9]*)  /viewtopic.php?f=$1&t=$2&$query_string last;

rewrite ^/forum/([0-9]*)/start/([0-9]*) /viewforum.php?f=$1&start=$2&$query_string last;

rewrite ^/forum/([0-9]*)/ /viewforum.php?f=$1&$query_string last;

rewrite ^/forum/([0-9]*) /viewforum.php?f=$1&$query_string last;

rewrite ^/post/([0-9]*)/$ /viewtopic.php?p=$1&$query_string last;


