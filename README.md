# [Dashing](http://shopify.github.com/dashing)

Dashing is a Sinatra based framework that lets you build beautiful dashboards. It looks especially great on TVs.

[Check out the homepage](http://shopify.github.com/dashing).

# License
Distributed under the [MIT license](https://github.com/Shopify/dashing/blob/master/MIT-LICENSE)

# Enabling Remote Backups

By Akash Manohar [HashNuke](https://github.com/HashNuke/).

Change your app's gem source in the Gemfile to this:

```ruby
gem 'dashing', github: "exotel/dashing", branch: "remote_backup"
```

Once you update your bundle, run the following commands:

```shell
bundle update
git commit -am "Update Gemfile to use exotel fork of dashing"
heroku config:set remote_backup_url="<your endpoint to persist data>"
git push heroku master
```

Your end point can be similar to this

```php
<?php
$store_file_path = '/tmp/dashboardtmp/file';
$request_method = $_SERVER['REQUEST_METHOD'];

if ($request_method == "DELETE") {
        $fp = fopen($store_file_path, "w");
        fwrite($fp, "");
        fclose($fp);
}
if ($request_method == "POST") {
        if (isset($_POST['data'])) {
                $fp = fopen($store_file_path, "w");
                fwrite($fp, $_POST['data']);
                fclose($fp);
        }
}
if ($request_method == "GET") {
        $contents = file_get_contents($store_file_path);
        echo $contents;
}
```
