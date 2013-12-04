[![Code Climate](https://codeclimate.com/github/janjiss/conred.png)](https://codeclimate.com/github/janjiss/conred)
[![Build Status](https://travis-ci.org/janjiss/conred.png?branch=master)](https://travis-ci.org/janjiss/conred)

# Conred

In every project we have common things like video 
embedding from url, user input displaying, formatting, trimming stripping,
external url protocol adding and all that nasty stuff that we write in our apps. 
These are the cases where Conred saves the day. 

## Installation

Add this line to your application's Gemfile:

    gem 'conred'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install conred

## Usage

### Iframe generator for Youtube and Vimeo videos:

    c = Conred::Video.new(
      video_url: "http://www.youtube.com/watch?v=tNtW9pGFPTA&feature=plcp", 
      width: 285, 
      height: 185,
      error_message: "Video url is invalid"
    )
    
__NOTE:__ This is new constructor type as of version 0.3.0. 

Then you can get your ready embed code like this (Conred will recognize video provider by itself):
    
    c.code
    
You can also check if it is youtube or vimeo video like this:

    c.youtube_video? ==> true
    c.vimeo_video? ==> false
    
Or if it exists:

    c.exists? ==> true

### General helpers for rails app
    
If you wish to use text helpers then in your application_helper add this include line:

    include Conred::Helpers

Now you have these methods available to you:

Sanitizes all html and trims content if count is provided:
    
    sanitize_and_trim("<html>string with", 10) => "string ..."
    
Sanitizes body, allowed tags are(p a strong ul ol li blockquote strike u em):

    sanitize_body("<html><strong>string</strong> <p>with<p></html>") => "<strong>string</strong> <p>with<p>"
    
External link formatting

    external_url("www.google.com") => "http://www.google.com"

## Contributing

1. Fork it
2. Write your feature
3. Create tests for it (Important!)
4. Create new Pull Request
5. Be happy

## Thank you's

I would like to thank these guys for contributing:
@alexcp
@barisbalic
@danielnolan
