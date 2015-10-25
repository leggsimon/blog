---
layout: post
title:  "Dependency Injection"
date:   2015-10-25 17:57:05
categories: ruby concepts ood
---


### Dependency Injection

During my course we were taught a little bit about Dependency Injection and it's uses in Object Oriented Design. To be completely honest I didn't really understand it at first, I vaguely understood how you'd do it but not really why you'd do it.

This week however I was helping my mentee Jamie. who is currently on his week 2 of Makers Academy and is doing a OOD kata based around [Oystercards](https://en.wikipedia.org/wiki/Oyster_card) (a card you can top-up to pay for travel in London). I was helping him with a few things but couldn't help but notice his `Journey` class;

```ruby
class Journey

  MIN_FARE = 1
  PENALTY_FARE = 6

  def initialize
    @entry = nil
    @exit  = nil
  end

  def in_journey?
    !!entry && @exit.nil?
  end

  def entry_station(station)
    @entry = Station.new(station)
  end

  def exit_station(station)
    @entry = Station.new(station)
  end

  def fare
    ( !!@entry && !!@exit ) ? MIN_FARE : PENALTY_FARE
  end
end
```

I looked at this and thought _"This would be a great place to use Dependency Injection!"_. I explained to Jamie that the `Journey` now becomes dependent on the `Station` class.

I thought, _"But a journey isn't only for trains. What if I wanted to use buses or riverboats?"_. So how might that look?

```ruby
class Journey

  MIN_FARE = 1
  PENALTY_FARE = 6

  attr_reader :entry_point, :exit_point

  def initialize(entry_point, exit_point)
    @entry_point = entry_point
    @exit_point  = exit_point
  end

  ...

end
```

This way you can inject any type of stop/station/pier you want and as long as it can respond to whatever methods you decide to use it the `Journey` class, you might want a `.zone` method that returns which travel zone it's in. As long as the stop/station/pier has a `.zone` method you could inject it in.

Now we can create any type of journey easily.

```
euston = TubeStation.new(:euston)
charing_cross = TubeStation.new(:charing_cross)

tube_journey = Journey.new(euston, charing_cross)
```
```
trafalgar_square = BusStop.new(:trafalgar_square)
oxford_circus = BusStop.new(:oxford_circus)

bus_journey = Journey.new(trafalgar_square, oxford_circus)
```
```
greenwich_pier = Pier.new(:greenwich_pier)
embankment_pier = Pier.new(:embankment_pier)

riverboat_journey = Journey.new(greenwich_pier, embankment_pier)
```

The good thing now is that our `Journey` class can be used for so much more and is therefore scalable. We might've wanted to just start with Stations but now, because you just 'inject' whichever class you do want you could use it for any type of journey in the future.

That is of course just one, very simple example of how Dependency Injection could be used but I think it's one that is quite easy to understand. I read a lot of stuff about it and I think this is quite a nice way of displaying how it can be used.
