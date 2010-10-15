# Mixpanel API Client (for API version 2.0)

Ruby access to the [Mixpanel](http://mixpanel.com/) web analytics tool.


## Installation

    gem install mixpanel_client


## New Usage

    require 'rubygems'
    require 'mixpanel_client'

    config = {'api_key' => 'changeme', 'api_secret' => 'changeme'}

    client = Mixpanel::Client.new(config)

    # Get all results for 'test-event' in the last 24 hours
    data = client.request do
      resource 'events'
      event    '["test-event"]'
      type     'general'
      unit     'hour'
      interval  24
    end
    puts data.inspect

    # Get the top property names for 'test-event'
    data = client.request do
      resource 'events/properties/top'
      event    '["test-event"]'
      type     'general'
    end
    puts data.inspect


## Old Usage (versions prior to 0.5.0)

__NOTE: This old usage is deprecated and will be removed in future versions.__

    require 'rubygems'
    require 'mixpanel_client'

    config = {:api_key => 'changeme', :api_secret => 'changeme'}

    api = Mixpanel::Client.new(config)

    # Example without an endpoint
    data = api.request(nil, :events, {
      :event    => '["test-event"]',
      :unit     => 'hour',
      :interval =>  24
    })
    puts data.inspect

    # Example with an endpoint and method
    data = api.request(:events, :top, {
      :type    => 'general'
    })
    puts data.inspect


## Copyright

Copyright (c) 2009+ Keolo Keagy. See LICENSE for details.
