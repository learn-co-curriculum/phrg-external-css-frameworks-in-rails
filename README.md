# External CSS Libraries In Rails

## Outline
Loading stylesheets into our application can be done many different ways in Rails. We can use HTML link tags for CSS files located on another server. We can place third party CSS files in our vendor folder.  We can also use gems to load the CSS frameworks we need like Twitter Bootstrap. 

## External Stylesheets
Not all of our stylesheets need to be loaded from the assets directory. It can be benificial to load these stylesheets from a CDN. This can save us bandwidth and help with download speeds for users throughout the world. To load CSS like this, we create HTML link tags in the `<head>` of our application layout file.

```html
<head>
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" />
</head>
```

## Vendor Assets
Managing a lot of different third party CSS files can be hard. We may forget which files are for what CSS frameworks. Also, seperate link tags mean these files will need to be downloaded one by one and this will slow page load times. At some point, we will probably decide to have these external CSS files to be internal CSS files.

We don't really want to clutter our main `assets/stylesheets` folder with CSS maintained by others. Rails provides the `vendor/assets/stylesheets` folder for these types of CSS files. We can place our third party CSS frameworks in here and add them to our CSS manifest file. We get the added benifit of having all of these external CSS files combined into one file with all our application CSS files.

## Gems
Manually adding CSS to our vendor directory can be cumbersome and hard to maintain. New version of the CSS frameworks are released and it's easy to fall behind. Luckly for us, many of the popular CSS frameworks have a gems. These gems package the CSS files and when installed, add them to our asset path allowing us to require them inside of our CSS manifest file.

Let's install the Twitter Bootstrap gem in our Gemfile. You will need to add 'gem "bootstrap-sass"' to your Gemfile and run `bundle install`. Once that completes you are able to add `*= require bootstrap` to our manifest file. Now Bootstrap will be loaded by Rails. We can also use bundler to update Twitter Bootstrap when new versions are released. Handling updating is particular helpful for bigger CSS frameworks like Bootstrap that have many CSS files.

##References
- [Bootstrap SASS Gem](https://github.com/twbs/bootstrap-sass)

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/external-css-frameworks-in-rails' title='External CSS Libraries In Rails'>External CSS Libraries In Rails</a> on Learn.co and start learning to code for free.</p>
