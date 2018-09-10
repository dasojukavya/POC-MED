#!/bin/ruby

require 'net/http'
require 'openssl'
require 'uri'
require 'json'
require 'optparse'

def get_post_response(uri1, formdata, token)
    uri = URI.parse(uri1)
        response = ''
    Net::HTTP.start(uri.host, uri.port,
                    use_ssl: uri.scheme == 'https',
                    verify_mode: OpenSSL::SSL::VERIFY_NONE) do |http|


      request = Net::HTTP::Post.new(uri.request_uri)
      request['Content-Type'] = 'application/json'
      request['Authorization'] = 'token ' + token
          if formdata != ''
              request.body=formdata
          end
      response = http.request(request)
          puts "Response is", response.body
    end
    return true if response.code == '201'
    false
end
