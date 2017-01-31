## Rust 2017 Roadmap

As part of [RFC 1728](https://github.com/rust-lang/rfcs/pull/1728), each year
the Rust community puts together a *roadmap* laying out a vision for
improvements to Rust over the course of the year. The 2017 roadmap was decided
in [RFC 1774](https://github.com/rust-lang/rfcs/pull/1774).

The issues in this repository track the progress on our 2017 roadmap.

**Only Rust subteam members should create new issues in this repo**. If you
believe a project should be added within the tracker, please leave a comment on
the appropriate "parent" issue, i.e. one of the issues linked below. And in
general, feel free to use comments to ask questions, pitch ideas, or mention
updates that need to be made!

There are issues for each of the vision statements:

* [Rust should have a lower learning curve](https://github.com/aturon/rust-roadmap/issues/3)
* [Rust should have a pleasant edit-compile-debug cycle](https://github.com/aturon/rust-roadmap/issues/1)
* [Rust should provide a solid, but basic IDE experience](https://github.com/aturon/rust-roadmap/issues/2)
* [Rust should provide easy access to high quality crates](https://github.com/aturon/rust-roadmap/issues/9)
* [Rust should be well-equipped for writing robust, high-scale servers](https://github.com/aturon/rust-roadmap/issues/10)
* [Rust should have 1.0-level crates for essential tasks](https://github.com/aturon/rust-roadmap/issues/11)
* [Rust should integrate easily into large build systems](https://github.com/aturon/rust-roadmap/issues/12)
* [Rust's community should provide mentoring at all levels](https://github.com/aturon/rust-roadmap/issues/13)

and for our two areas of exploration:

* [Integration with other languages, running the gamut from C to JavaScript](https://github.com/aturon/rust-roadmap/issues/14)
* [Usage in resource-constrained environments](https://github.com/aturon/rust-roadmap/issues/15)

Each of the above issues link to a number of other *project* issues, which give
points of contact and other information about the status of specific projects
working to achieve one of our goals. You can see the list of all projects [here](https://github.com/aturon/rust-roadmap/issues?q=is%3Aissue+is%3Aopen+label%3AProject).

Finally, each subteam has a dedicated roadmap issue, spelling out areas of
activity beyond those included in the formal Rust roadmap:

- [Lang team](https://github.com/aturon/rust-roadmap/issues/18)
- [Libs team](https://github.com/aturon/rust-roadmap/issues/19)
- [Compiler team](https://github.com/aturon/rust-roadmap/issues/21)
- [Community team](https://github.com/aturon/rust-roadmap/issues/22)
- [Docs team](https://github.com/aturon/rust-roadmap/issues/20)
- [Tools team](https://github.com/aturon/rust-roadmap/issues/23)

## Roadmap rationale

The full rationale for the roadmap is spelled out in
[RFC 1774](https://github.com/rust-lang/rfcs/pull/1774), but we'll recap the
high-level framing here.

There's no end of possible improvements to Rust—so what do we use to guide our
thinking?

The core team has tended to view our strategy not in terms of particular features or
aesthetic goals, but instead in terms of **making Rust successful while staying
true to its core values**. This basic sentiment underlies much of the proposed
roadmap, so let's unpack it a bit.

### Making Rust successful

#### The measure of success

What does it mean for Rust to be successful? There are a lot of good answers to
this question, a lot of different things that draw people to use or contribute
to Rust. But regardless of our *personal* values, there's at least one clear
measure for Rust's broad success: **people should be using Rust in
production and reaping clear benefits from doing so**.

- Production use matters for the obvious reason: it grows the set of
  stakeholders with potential to invest in the language and ecosystem. To
  deliver on that potential, Rust needs to be part of the backbone of some major
  products.

- Production use measures our *design* success; it's the ultimate reality
  check. Rust takes a unique stance on a number of tradeoffs, which we believe
  to position it well for writing fast and reliable software. The real test of
  those beliefs is people using Rust to build large, production systems, on
  which they're betting time and money.

- The *kind* of production use matters. For Rust to truly be a success, there
  should be clear-cut reasons people are employing it rather than another
  language. Rust needs to provide crisp, standout benefits to the organizations
  using it.

The idea here is *not* about "taking over the world" with Rust; it's not about
market share for the sake of market share. But if Rust is truly delivering a
valuable new way of programming, we should be seeing that benefit in "the real
world", in production uses that are significant enough to help sustain Rust's
development.

That's not to say we should expect to see this usage *immediately*; there's a
long pipeline for technology adoption, so the effects of our work can take a
while to appear. The framing here is about our long-term aims. We should be
making investments in Rust today that will position it well for this kind of
success in the future.

#### The obstacles to success

At this point, we have a fair amount of data about how Rust is reaching its
audience, through the [2016 survey], informal conversations, and explicit
outreach to (pre-)production shops (writeup coming soon). The data from the
survey is generally corroborated by these other venues, so let's focus on that.

[2016 survey]: https://blog.rust-lang.org/2016/06/30/State-of-Rust-Survey-2016.html

We asked both current and potential users what most stands in the way of their
using Rust, and got some pretty clear answers:

- 1 in 4: learning curve
- 1 in 7: lack of libraries
- 1 in 9: general “maturity” concerns
- 1 in 19: lack of IDEs (1 in 4 non-users)
- 1 in 20: compiler performance

None of these obstacles is directly about the core language or `std`; people are
generally happy with what the language offers today. Instead, the connecting
theme is *productivity*—how quickly can I start writing real code? bring up a
team? prototype and iterate? debug my code? And so on.

In other words, our primary challenge isn't making Rust "better" in the
abstract; it's making people *productive* with Rust. The need is most pronounced
in the early stages of Rust learning, where we risk losing a large pool of
interested people if we can't get them over the hump. Evidence from the survey
and elsewhere suggests that once people do get over the initial learning curve,
they tend to stick around.

So how do we pull it off?

#### Core values

Part of what makes Rust so exciting is that it attempts to eliminate some
seemingly fundamental tradeoffs. The central such tradeoff is between safety
and speed. Rust strives for

- uncompromising reliability
- uncompromising performance

and delivers on this goal largely thanks to its fundamental concept of
ownership.

But there's a problem: at first glance, "productivity" and "learnability" may
seem at odds with Rust's core goals. It's common to hear the refrain that
"fighting with the borrow checker" is a rite of passage for Rustaceans. Or that
removing papercuts would mean glossing over safety holes or performance cliffs.

To be sure, there are tradeoffs here. But as above, if there's one thing the
Rust community knows how to do, it's bending the curve around tradeoffs—memory
safety without garbage collection, concurrency without data races, and all the
rest. We have many examples in the language where we've managed to make a
feature pleasant to use, while also providing maximum performance and
safety—closures are a particularly good example, but there are
[others](https://internals.rust-lang.org/t/roadmap-2017-productivity-learning-curve-and-expressiveness/4097).

And of course, beyond the core language, "productivity" also depends a lot on
tooling and the ecosystem. Cargo is one example where Rust's tooling provides a
huge productivity boost, and we've been working hard on other aspects of
tooling, like the
[compiler's error messages](https://blog.rust-lang.org/2016/08/10/Shape-of-errors-to-come.html),
that likewise have a big impact on productivity. There's so much more we can be
doing in this space.

In short, **productivity should be a core value of Rust**. By the end of 2017,
let's try to earn the slogan:

- Rust: fast, reliable, productive—pick three.
