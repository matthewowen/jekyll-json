## NOT MAINTAINED

I hope this helps you, but I have to be honest: I'm not really working on this anymore, and so I can't rule out that there are things that don't work right etc etc etc. If you want to contribute or fork or anything, please do! But I just don't really have the bandwidth for bugfixes, let alone feature requests! Sorry :(.

# Jekyll JSON

Jekyll JSON turns YAML config into JSON, so that you can use it in Javascript.

Passed a YAML key, it'll return a JSON, combining the page specific YAML with any config in _config.yml (using the value set on the page wherever there's a conflict).

## Usage

Plonk jekyll_json.rb in your _plugins directory.

Use the tag like this:

    {% yaml_to_json yaml_key_goes_here %}

## An example

In _config.yml:

    mapping:
        provider: google_js
        api_key: 123456
        zoom: 10
        dimensions:
            width: 600
            height: 400

In a page's front matter:

    mapping:
        latitude: 0
        longitude: 0
        dimensions:
            width: 500
            height: 500

In your layout:

    <script type="text/javascript">
        var some_object = {% yaml_to_json mapping %};
    </script>

Returns:

    <script type="text/javascript">
        var some_object = {
            "longitude":0,
            "api_key":123456,
            "dimensions":{
                "height":500,
                "width":500
            },
            "provider":"google_js",
            "latitude":0,
            "zoom":10
        };
    </script>

    
