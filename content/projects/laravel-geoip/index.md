---
title: Laravel 5 Geoip
template: default.twig
images: /uploads/projects/laravel-geoip
github: http://github.com/torann/laravel-geoip
---
{% include 'project_header.twig' with {'intro': 'Determine the geographical location of website visitors based on their IP addresses.'} %}

<div class="wrapper">
    <h2>Installation</h2>

    <p>To get the latest version of GeoIP simply require it in your <code>composer.json</code> file.</p>

<pre><code>"torann/geoip": "dev-master"
</code></pre>

    <p>You'll then need to run <code>composer install</code> to download it and have the autoloader updated.</p>

    <p>Once GeoIP is installed you need to register the service provider with the application. Open up <code>config/app.php</code> and find the <code>providers</code> key.</p>

<pre><code>'providers' => array(
    'Torann\GeoIP\GeoIPServiceProvider',
)
</code></pre>

    <p>GeoIP also ships with a facade which provides the static syntax for creating collections. You can register the facade in the <code>aliases</code> key of your <code>config/app.php</code> file.</p>


<pre><code>'aliases' => array(
    'GeoIP' => 'Torann\GeoIP\GeoIPFacade',
)
</code></pre>

    <p>Create configuration file using artisan</p>

    <pre><code>$ php artisan vendor:publish</code></pre>

    <h2>Usage</h2>

    <p>Get the location data for a website visitor:</p>

    <pre><code>$location = GeoIP::getLocation();</code></pre>

    <blockquote>
        <p>When an IP is not given the <code>$_SERVER["REMOTE_ADDR"]</code> is used.</p>
    </blockquote>

    <p>Getting the location data for a given IP:</p>

    <pre><code>$location = GeoIP::getLocation('232.223.11.11');</code></pre>

    <h3>Example Data</h3>

<pre><code>array (
    "ip"           => "232.223.11.11",
    "isoCode"      => "US",
    "country"      => "United States",
    "city"         => "New Haven",
    "state"        => "CT",
    "postal_code"  => "06510",
    "lat"          => 41.28,
    "lon"          => -72.88,
    "timezone"     => "America/New_York",
    "continent"    => "NA",
    "default"      => false
);
</code></pre>

    <h4>Default Location</h4>

    <p>In the case that a location is not found the fallback location will be returned with the <code>default</code> parameter set to <code>true</code>. To set your own default change it in the configurations <code>config/geoip.php</code>.</p>

    <h2>Services</h2>

    <h3><a href="http://www.maxmind.com">MaxMind</a></h3>

    <ul>
        <li>
            <strong>Database Service</strong>: To use the database version of MaxMind services download the <code>GeoLite2-City.mmdb</code> from <a href="http://dev.maxmind.com/geoip/geoip2/geolite2/">http://dev.maxmind.com/geoip/geoip2/geolite2/</a> and extract it to <code>/database/maxmind/</code>. And that's it.</li>
    </ul>
</div>