Watchiot Docs
----------------

This project is using Jekyll to render the **Watchiot Docs Api**. For more details about Jekyll please visit the [official site](https://jekyllrb.com/)

If you want to see this project on production, please visit [http://docs.watchiot.org/](http://docs.watchiot.org/)

## Install and Run

```shell
$ gem install jekyll
$ git clone https://github.com/watchiot/watchiot-docs.git
$ cd watchiot-docs
$ bundle exec jekyll build
$ bundle exec jekyll server
```
Now you can access to the url 

[http://localhost:4000/](http://localhost:4000/)

## Contributing

* Report a bug.
* Report bad description. 
* Report incomplete description.
* Report grammatical errors or orthographic errors.
* Creating a new post and send us a PR too.
* Add other language docs, like [fr, ru, ch] etc.
 
### How add other language docs

* Fork the watchiot-docs repo
* Into the _config.yaml
* Edit ```languages: ["en", "es"]``` adding the new lanaguage, example add "fr" ```languages: ["en", "es", "fr"]```
* Into the i18n folder make a new folder called *fr*
* Into the *fr* folder copy and paste the same files into the folder *i18n/en*
* Then only you have to edit the posts using the new language.
* The last step is add *fr* into the selector view language into the file *_includes/post.html*
 
```html
<div class="post">
    {% if site.lang == "en" %}
    {% capture link %}{{ site.baseurl_root }}/es{{ page.url}}{% endcapture %}
    <div align="right">
        <a href="{{ link }}" >{% t global.spanish %}</a><span class="separator"> &bull; </span>
    </div>
    {% elsif site.lang == "es" %}
    {% capture link1 %}{{ site.baseurl_root }}{{ page.url  }}{% endcapture %}
    <div align="right">
        <a href="{{ link1 }}" >{% t global.english %}</a><span class="separator"> &bull; </span>
    </div>
    
    <!-- Here you new language selector -->
    
    {% endif %}
</div>
```
* And the end send to us a pull request. 

## License

(The MIT License)

Copyright (c) 2016 WatchIoT

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

