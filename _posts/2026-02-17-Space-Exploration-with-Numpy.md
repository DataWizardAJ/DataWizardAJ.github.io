---
layout: post
title: Calculating Volumes of 1 Million Theoretical Planets with Python
image: "/posts/1m_Planets.jpg"
tags: [Numpy, Planets]
---

In this post I'm going to share a Python program which instantly calculates the volumes of 1 million theoretical Planets, using Numpy.

There are an infinite number of Planets, the vast majority of which are completely unknown to us, including their Size.

This project therefore provides a useful array of volumes of theoretical Planets.

Ready? Then let's venture on!

---

First, let's just calculate the Volume of a sphere with a known Radius of 5, just to check Python and Numpy are 'Playing ball'...

To get the Volume, we multiply the Radius cubed by 4/3rds of Pi

```ruby
r = 5
volume = 4/3 * np.pi * r**3
```

Great, that's working as intended!

Next, let's just use it to check the Volumes of the planets in our Solar System for fun!

Taking a list of the Radii (in Km) of each Planet and passing that into the volume equation.

```ruby
radii = np.array([2439.7,6051.8,6371,3389.7,69911,58232,25362,24622])
volumes = 4/3 * np.pi * radii**3
```

Wow, the mind boggles at these numbers.

Now we know it's working as intended, we can really get stuck in and get stargazing.

We don't know how big all the planets in the Universe are, but we have some numbers to work with.

For example, the smallest known planet is a little-known rock called Kepler-37b, at a radius of 0.31 times that of Earth. This equates to 0.31 * 6,871km = 1,975km.

Great, so that gives us a useful lower limit to work with. So, what about the upper limit?

The largest known Planet is a Gas Giant called ROXs 42 Bb, which is nearly 500 light years away! ROXs 42 Bb is 1.12 times the radius of the largest Planet in our Solar System, i.e Jupiter. This gives us a radius of 1.12 * 69911km = 78,300km.

Fantastic! We now have our upper limit and lower limit, which means we're ready to go.

To make it easier for ourselves, let's save this calculation as a Function that we'll call planet_volumes.

```ruby
def planet_volumes(radius):
    v = 4/3 * np.pi * radius**3
    return v
```

Now that we have our Function, let's create our array of A MILLION theoretical planet radii to pass into it.

```ruby
radii = np.random.randint(1975,78300, 1000000)

planet_volumes(radii)
```

Wow...

There we go, we now have the Volumes of a MILLION theoretical Planets. What can we do witht that?

Well, we can use it to calculate the theoretical volumes of precious minerals, in a future where we have achieved interplanetary travel. Or we can use it to calculate gravitational pulls of theoritcal space travel through uncharted areas of space.

We can do some really exciting things with this incredibly fast calculation!

Just as a consideration, there is a chance that this may return some negative values if the values become too large for int32. If we want to guard against this, we can make sure to cast it as a Float directly within the Function.

To do this we would simply write the Function as follows.

```ruby
def planet_volumes(radius):
    v = 4/3 * np.pi * radius.astype(float)**3
    return v
```

This should insulate us from negative errors.

What an exciting trip through Space that was!
