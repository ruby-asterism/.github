# Asterism

**One network of Ruby objects** across CRuby, mruby / PicoRuby boards, the
browser and ROS 2, on [Zenoh](https://zenoh.io/).

Call a Ruby object on another machine as if it were local, find who is on
the network as they come and go, and talk to ROS 2 nodes (rmw_zenoh) from
Ruby, with the same Ruby layers on a PC, a microcontroller and a web page.

```ruby
require "asterism"

Asterism.connect("tcp/192.0.2.2:7447", node: "mypc", app: "demo") do |net|
  net.on_join { |node| puts "joined #{node}" }
  net["fmruby-aaaaaa/demo/screen"].say("hello")   # a method on a board
  net.run
end
```

## Repositories

| Repository | What |
|---|---|
| [asterism](https://github.com/ruby-asterism/asterism) | The Ruby layers (remote objects, ROS 2 messages, profiles), shared by every Ruby. `gem install asterism` |
| [asterism-zenoh](https://github.com/ruby-asterism/asterism-zenoh) | The Zenoh binding for CRuby (over zenoh-c) |
| [picoruby-asterism-zenoh](https://github.com/ruby-asterism/picoruby-asterism-zenoh) | The Zenoh binding for mruby / PicoRuby boards (over zenoh-pico) |
| [asterism-console](https://github.com/ruby-asterism/asterism-console) | A Rails app that shows the network as a live graph: nodes, objects, ROS 2 topics, recording and rewind |

Asterism grew out of [Family mruby](https://github.com/family-mruby), whose
boards, simulator and browser build join the network as Asterism nodes.
