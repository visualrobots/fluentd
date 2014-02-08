= Fluentd

{<img src="https://travis-ci.org/fluent/fluentd.png" />}[https://travis-ci.org/fluent/fluentd] {<img src="https://codeclimate.com/github/fluent/fluentd.png " />}[https://codeclimate.com/github/fluent/fluentd]

Fluentd is an event collector system. It is a generalized version of syslogd, which handles JSON objects for its log messages.

== Architecture

Fluentd collects events from various data sources and writes them to files, database or other types of storages:

    
    Web apps  ---+                 +--> file
                 |                 |
                 +-->           ---+
    /var/log  ------>  Fluentd  ------> mail
                 +-->           ---+
                 |                 |
    Apache    ----                 +--> Fluentd
    

Fluent also supports log transfer:

    
    Web server
    +---------+
    | Fluentd -------
    +---------+|     |
     +---------+     |
                     |
    Proxy server     |    Log server, Amazon S3, HDFS, ...
    +---------+      +--> +---------+
    | Fluentd ----------> | Fluentd ||
    +---------+|     +--> +---------+|
     +---------+     |     +---------+
                     |
    Database server  |
    +---------+      |
    | Fluentd ---------> mail
    +---------+|
     +---------+
    

An event consists of *tag*, *time* and *record*. Tag is a string separated with '.' (e.g. myapp.access). It is used to categorize events. Time is a UNIX time recorded at occurrence of an event. Record is a JSON object.


== Quick Start

  $ gem install fluentd
  $ # install sample configuration file to the directory
  $ fluentd -s conf
  $ fluentd -c conf/fluent.conf &
  $ echo '{"json":"message"}' | fluent-cat debug.test

== Sign Up For Our Newsletters and Learn More

{Sign up for our newsletters}[http://go.treasuredata.com/Fluentd_education] and get the latest updates and bug fixes right in your inbox.

== Meta

Web site::  http://fluentd.org/
Documents:: http://docs.fluentd.org/
Source repository:: http://github.com/fluent
Discussion:: http://groups.google.com/group/fluentd
Author:: Sadayuki Furuhashi
Copyright:: (c) 2011 FURUHASHI Sadayuki
License:: Apache License, Version 2.0

== Contributors:

Patches contributed by {those people}[https://github.com/fluent/fluentd/contributors].

{<img src="https://ga-beacon.appspot.com/UA-24890265-6/fluent/fluentd" />}[https://github.com/fluent/fluentd]
