# Installing WordHat

## Requirements

WordHat requires [PHP](https://php.net/) (version 5.6+), [Composer](https://getcomposer.org/), and a [WordPress](https://wordpress.org/) site to test (version 4.8+).

We strongly recommend using [WP-CLI](https://wp-cli.org/)[^1] \(version 1.3.0+), and the standalone version of [Selenium](http://docs.seleniumhq.org/download/)[^2].


## Installation

<ol>

<li>Create a folder for your tests. From a terminal:
    <pre><code>mkdir project
cd project</code></pre>
</li>

<li>Tell <a href="https://getcomposer.org/">Composer</a> to download WordHat:
    <pre>composer require --dev paulgibbs/behat-wordpress-extension behat/mink-goutte-driver behat/mink-selenium2-driver</pre>
</li>

<li>Copy WordHat's sample configuration file into your <code>project</code> folder and rename it:
    <pre><code>cp vendor/paulgibbs/behat-wordpress-extension/behat.yml.dist behat.yml</code></pre>
</li>

<li>Edit your <code>behat.yml</code> and update the <code>base_url</code> setting with the URL of the website that you intend to test.
     <div class="admonition tip">
        <p class="admonition-title">Tip</p>
        <p>You can also declare a WP CLI alais at this point if you have a more exotic install configuration</p>
    </div>
</li>

<li>Initialise <a href="http://behat.org">Behat</a>:
    <pre><code>vendor/bin/behat --init</code></pre>

    <div class="admonition tip">
        <p class="admonition-title">Tip</p>
        <p>This will create a <code>features/</code> folder for your <a href="http://docs.behat.org/en/latest/user_guide/features_scenarios.html#features">Features (tests)</a>, and a new <a href="http://docs.behat.org/en/latest/user_guide/context.html">Context class</a>. These will come in handy later!</p>
    </div>
</li>

<li>To confirm that everything is set up correctly, run:
    <pre><code>vendor/bin/behat -dl</code></pre>
    If it worked, you will see a list of text that looks a little like the following (but much longer):
    <pre><code>Given I am an anonymous user
Given I am not logged in
Given I am logged in as a user with the :role role(s)
Given I am logged in as :name
&hellip;</pre></code>
</li>

</ol>


## Next steps

Now that you have WordHat set up, we recommend reading our [introduction to Behat](behat-intro.md) to help you learn the basics before you start writing tests for your site.


[^1]:
    The WP-CLI executable *must* be named `wp` and be within your system's <a href="https://en.wikipedia.org/wiki/PATH_(variable)" id="WP-CLI">$PATH</a>.

[^2]:
    Recommended for testing <a href="http://mink.behat.org/en/latest/guides/drivers.html" id="SEL">websites that require Javascript</a>. It requires the [Mink Selenium2 driver](https://packagist.org/packages/behat/mink-selenium2-driver), which we include in the installation instructions above.
