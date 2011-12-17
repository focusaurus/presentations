# Notes for Rails asset pipeline lightning talk

[Peter Lyons](http://peterlyons.com) at [Denver Hack Nite](http://hacknite.com) 2011-12-15

* http://guides.rubyonrails.org/asset_pipeline.html
* Asset pipeline is about performance: fewer HTTP requests. Aggressive caching.
* 3 Content types: images, CSS, JavaScript
* Configuration options
    * enable
    * compile
    * digest
    * compress
* Rake tasks to precompile
* javascript_include_tag "someasset"
* image_tag "someasset"
* stylesheet_link_tag "someasset"
* Uses sprockets gem as the underlying engine
* Comment syntax to declare load order/dependencies
* config.assets.precompile += ['admin.js', 'admin.css', 'swfObject.js']

.

    // This is a manifest file that'll be compiled into including all the files listed below.
    // Add new JavaScript/Coffee code in separate files in this directory and they'll automatically
    // be included in the compiled file accessible from http://example.com/assets/application.js
    // It's not advisable to add code directly here, but if you do, it'll appear at the bottom of the
    // the compiled file.
    //
    //= require ./lib/jquery
    //= require ./lib/jquery-ui
    //= require ./lib/jquery-placehold
    //= require ./linkzie
    //= require ./comments

.

    /*
     * This is a manifest file that'll automatically include all the stylesheets available in this directory
     * and any sub-directories. You're free to add application-wide styles to this file and they'll appear at
     * the top of the compiled file, but it's generally better to create a new file per style scope.
     *
     * These files should be explicitly ordered at the top as they are general
     *= require ./blueprint/reset_typography
     *= require ./jquery-ui-custom
     *= require ./shared
     *= require ./forms
     *
     * These files have tightly-bound selectors and thus order doesn't matter
     *= require ./categories
     *= require ./comments
     *= require ./errors
     *= require ./footer"