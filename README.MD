# Wordpress with api basic-auth

- create a wordpress server
- enable api
- api with authentication
- written by the ~~goodest~~ **BEST** siuga

## TOC
- [Wordpress with api basic-auth](#wordpress-with-api-basic-auth)
  * [TOC](#toc)
  * [Installation](#installation)
  * [LAMP troubleshoot](#lamp-troubleshoot)
  * [Testing](#testing)
    + [1. Create Post](#1-create-post)
    + [2. Get Post](#2-get-post)

## Installation

1. Download [Wordpress](https://tw.wordpress.org/download/releases/)
2. Unzip the wordpress zip then place into a server folder.
(example: /home/ubuntu/var/www)
3. Start a database of MYSQL with name "wordpress"
4. Go to <[http://example.com/wordpress/readme](http://localhost/wordpress/readme)> following the instrustion
5. The pre-config database should be working in the config setup.
6. Login the panel
7. Go to plugin
8. Install "**WordPress REST API Authentication**" from the plugin market
9. Enable the "**WordPress REST API Authentication**"
10. Go to "**WordPress REST API Authentication**" setting from sidebar
11. On "Configure API Authentication" tab, select **Basic Auth** as  **Authentication Method**  and **Username : Password** as **Basic Auth Authentication Key**
12. Save configuration
13. Complete!

## Testing

### 1. Create Post

Endpoint:   
(http://example.com/wordpress/wp-json/wp/v2/posts)
Method:   
**POST**
Authorization:  
**Basic Auth** - `Username:Password`
Header:  
```JSON
{
	"Content-Type":"application/json"
}
```

Body:
```JSON
{
	"date":"2019-11-29 16:00:00",
	"date_gmt":"2019-11-29 16:00:00",
	"status":"publish",
	"title":"PageTesto",
	"content":"Standart Content"
}
```

Response:
```JSON
{
	"id": 5,
	"date": "2019-11-29T16:00:00",
	"date_gmt": "2019-11-29T08:00:00",
	"guid": {
		"rendered": "http://localhost/wordpress/?p=5",
		"raw": "http://localhost/wordpress/?p=5"
	},
	"modified": "2019-11-29T16:00:00",
	"modified_gmt": "2019-11-29T08:00:00",
	"password": "",
	"slug": "pagetesto",
	"status": "future",
	"type": "post",
	"link": "http://localhost/wordpress/?p=5",
	"title": {
		"raw": "PageTesto",
		"rendered": "PageTesto"
	},
	"content": {
		"raw": "Standart Content",
		"rendered": "<p>Standart Content</p>\n",
		"protected": false,
		"block_version": 0
	},
	"excerpt": {
		"raw": "",
		"rendered": "<p>Standart Content</p>\n",
		"protected": false
	},
	"author": 1,
	"featured_media": 0,
	"comment_status": "open",
	"ping_status": "open",
	"sticky": false,
	"template": "",
	"format": "standard",
	"meta": [],
	"categories": [1],
	"tags": [],
	"permalink_template": "http://localhost/wordpress/2019/11/29/%postname%/",
	"generated_slug": "pagetesto",
	"_links": {	
		"self": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"collection": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts"
			}
		],
		"about": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/types/post"
			}
		],
		"author": [
			{
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/users/1"
			}
		],
		"replies": [
			{
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/comments?post=5"
			}
		],
		"version-history": [
			{
				"count": 0,
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5/revisions"
			}
		],
		"wp:attachment": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/media?parent=5"
			}
		],
		"wp:term": [
			{
				"taxonomy": "category",
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/categories?post=5"
			},
			{
				"taxonomy": "post_tag",
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/tags?post=5"
			}
		],
		"wp:action-publish": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-unfiltered-html": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-sticky": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-assign-author": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-create-categories": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-assign-categories": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-create-tags": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-assign-tags": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"curies": [
			{
				"name": "wp",
				"href": "https://api.w.org/{rel}",
				"templated": true
			}
		]
	}
}
```

### 2. Get Post

Endpoint:   
(http://example.com/wordpress/wp-json/wp/v2/posts)
Method:   
**GET**
Authorization:  
Not Required
Header:  
Not Required
Body:
Not Required

Response:
```JSON
{
	"id": 5,
	"date": "2019-11-29T16:00:00",
	"date_gmt": "2019-11-29T08:00:00",
	"guid": {
		"rendered": "http://localhost/wordpress/?p=5",
		"raw": "http://localhost/wordpress/?p=5"
	},
	"modified": "2019-11-29T16:00:00",
	"modified_gmt": "2019-11-29T08:00:00",
	"password": "",
	"slug": "pagetesto",
	"status": "future",
	"type": "post",
	"link": "http://localhost/wordpress/?p=5",
	"title": {
		"raw": "PageTesto",
		"rendered": "PageTesto"
	},
	"content": {
		"raw": "Standart Content",
		"rendered": "<p>Standart Content</p>\n",
		"protected": false,
		"block_version": 0
	},
	"excerpt": {
		"raw": "",
		"rendered": "<p>Standart Content</p>\n",
		"protected": false
	},
	"author": 1,
	"featured_media": 0,
	"comment_status": "open",
	"ping_status": "open",
	"sticky": false,
	"template": "",
	"format": "standard",
	"meta": [],
	"categories": [1],
	"tags": [],
	"permalink_template": "http://localhost/wordpress/2019/11/29/%postname%/",
	"generated_slug": "pagetesto",
	"_links": {	
		"self": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"collection": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts"
			}
		],
		"about": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/types/post"
			}
		],
		"author": [
			{
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/users/1"
			}
		],
		"replies": [
			{
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/comments?post=5"
			}
		],
		"version-history": [
			{
				"count": 0,
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5/revisions"
			}
		],
		"wp:attachment": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/media?parent=5"
			}
		],
		"wp:term": [
			{
				"taxonomy": "category",
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/categories?post=5"
			},
			{
				"taxonomy": "post_tag",
				"embeddable": true,
				"href": "http://localhost/wordpress/wp-json/wp/v2/tags?post=5"
			}
		],
		"wp:action-publish": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-unfiltered-html": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-sticky": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-assign-author": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-create-categories": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-assign-categories": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-create-tags": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"wp:action-assign-tags": [
			{
				"href": "http://localhost/wordpress/wp-json/wp/v2/posts/5"
			}
		],
		"curies": [
			{
				"name": "wp",
				"href": "https://api.w.org/{rel}",
				"templated": true
			}
		]
	}
}
```