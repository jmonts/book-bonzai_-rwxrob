# 🌳Bonzai: Building Stateful Command Tree Interfaces with Go

*This book is under a state of active development and was taken from the documentation of the https://github.com/rwxrob/bonzai project recently.*

Trees of speakable, tab-completable subcommands (with no complicated dashes) are the new normal when creating modern tools. From terminal commands to chat bots, stateful command trees have proven to be the next evolutionary stage in efficient and powerful human-computer interfaces. Such interfaces can easily be used through a microphone or a keyboard by replacing "options" and "switches" with state and context.

## Getting Started

Copy or clone the example template:

👆 <https://github.com/rwxrob/bonzai-example>

Study the personal, script-replacing monolith/multicall that started it all:

👆 <https://github.com/rwxrob/z>

## Go Bonzai!

![logo](logo.png)

Yes, "banzai" is something people yell going into battle, and battle is exactly what it feels like to conquer your monstrous collection of shell scripts, completion bloated rc files, and man pages (if you even got that far).

"Bonsai" trees are well-manicured, meticulously crafted, miniature *real* trees that rival their larger cousins, much like a Bonzai composite command tree.

Bonzai trees are unlike anything you've likely encountered so far, no getopt dashes, no ugly commander interface language to learn, no 12637 lines of shell tab completion bloat to source before your command will complete, just well manicured nested-tab-complete-with-magical-aliases-enabled commands organized into rooted node trees for your command-line enjoyment. Your right-pinky will be particularly grateful.

## "It's spelled bonsai/banzai."

We know. The domains were taken. Plus, this makes it more unique and easier to find once you know the strange spelling we chose to use. Sorry if that triggers your OCD.

If you must know, the primary motivator was the similarity to a
well-manicured tree (since it is for creating trees of composite
commands).

The misunderstood word "banzai" is 'a traditional Japanese idiom
meaning "ten thousand years" of long life,' a cheer used in
celebrations like "Hurrah" or "Viva".' So combining the notion of a
happy, well-manicured, beautiful tree and "ten thousand years of
long life" works out just fine for us.

And, yes, Buckaroo Banzai was always a favorite. We like to think he
would use Bonzai today to make amazing things and last for a long time
to defeat evil aliens and save the world.

It turns out that the "call to war" associated with Bonzai is not
entirely without merit as well. Bonzai is excellent for unorthodox,
rapid applications development (instead of writing scripts) and makes
short work of creating offensive and defensive tool kits all wrapping
into one nice Go multicall binary, popular for building single-binary
Linux container distros like BusyBox and Alpine, as well as root kits,
and other security tools

## "Why not just use Cobra?"

We get this question a lot, the answer is --- honest.

Just because something is popular (or first) doesn't mean it was well
designed. In fact, often inferior designs are rushed to market just to
gain adoption. Cobra seems to suffer from this. Discerning developers
and engineers have been not-so-quietly complaining about Cobra's
horrible design for years. It's time for something new. Read on if you
want the specific reasons.

* **Cobra tab completion is wasteful and error-prone.**

  Cobra often requires sourcing thousands of lines of shell code every
  time you run a new shell that needs to use a Cobra command with shell
  tab completion (`kubectl` requires 12637). It is not uncommon for
  operations people to be sourcing 100s of thousands of lines of shell
  code just to enable basic completion that could have been enabled
  easily with `complete -C` instead. Bonzai manages all completion in Go
  instead of shell and therefore allows the modular addition of any
  number of Completers including the standard file completion as well as
  calculators, dates, and anything anyone can conceive of completing.
  Completion is not dependent on any underlying operating system. Any
  Bonzai command can provide its own completion algorithm or use one of
  the many already provided. Cobra can never do this.

* **Cobra is not designed to be a command compositor at all.**

  This is really unfortunate because the designers missed a golden
  opportunity. Bonzai branches can be imported and composed into other
  branches and monoliths with just a few lines of Go. Registries of
  Bonzai commands can be easily inferred from dependencies on the
  `bonzai` package and creators are free to compose their monoliths or
  multicall binaries from a rich eco-system of Bonzai branches and
  commands. Bonzai allows creation of Go multicall binary monoliths
  (like BusyBox) to be made easily, and from a diverse, modular,
  importable, composable sources. Such is simply not possible with Cobra
  and never will be.

* **Cobra suffers from broken boomer "getopt" design.**

  The world has finally realizing just how bad dashed arguments and
  options have always been for good human-computer interactions from the
  command line, perhaps because more regular people are using command
  line interfaces, like chat apps from their laptops and phones. People
  simply cannot remember all sorts of ungodly combinations of dashes and
  equals signs hoping things will just work, and they certainly cannot
  speak any getopt command into their phone and have it interpreted
  correctly. With Bonzai they can. Bonzai UX is universal whether it be
  from an Arch Linux command line or Slack app on an iPhone.

  Bonzai takes a no-dashes approach with aliases promoting cleaner,
  understandable command lines with context and promotion of domain
  specific languages (created with PEGN, scan.X, or others) that easily
  translate directly to chat and other command-line interfaces that most
  humans can use without even looking up the documentation, which, by
  the way, is embedded in any Bonzai command tree.

* **Cobra provides bad, brittle, command documentation.**

  Cobra documentation is virtually unreadable in source form. And Cobra
  provides no means of markup or use of color and doesn't even promote
  the same look and feel of manual page documentation.

  In contrast, Bonzai has its own subset of Markdown, BonzaiMark, which
  respects the well established readability of manual pages, and allows
  for the creation of elegant, templated documentation that can be
  viewed from the command line or easily from a local browser on the
  same computer running the command. Bonzai command documentation is as
  easy to read in source form as the documentation itself.

  Bonzai documentation is also dynamic. Rather than refer to a
  configuration file the path to that specific file can be dynamically
  included in the fully `text/template` enabled embedded documentation.
  Cobra doesn't have anything even close to this.

* **Cobra suffers from crushing technical debt.**

  The problems listed (and more) are never going to come out of Cobra.
  Because it is filled with bad design decisions and was rushed to
  market without serious consideration for its API, it is now doomed to
  never lose its warts (kinda like JavaScript). There is no possible way
  it can ever upgrade to address the very reasonable modern expectations
  for good command line user experiences. No wonder you never see people
  using Cobra for their replace-my-shell-scripts utilities. Cobra is
  simply horrible for this. Thankfully, Bonzai is a fresh, extensible,
  sustainable, human-friendly command compositor to take us into the
  future of command line interfaces.

* **Cobra interfaces are nearly impossible to test.**

  Ever tried creating tests for all the different Cobra option
  combinations? It's a case study in the science of exponential problem
  complexity. By using a rooted node tree of commands, which
  observe cached variables or singular configuration, Bonzai makes short
  work of writing even the highest-level of tests against the commands
  themselves as if they were run by a user.

## What People Are Saying

> "It's like a modular, multicall BusyBox builder for Go with built in
> completion and embedded documentation support."

> "The utility here is that Bonzai lets you maintain your own personal
> 'toolbox' with built in auto-complete that you can assemble from
> various Go modules. Individual commands are isolated and unaware of
> each other and possibly maintained by other people." (tadasv123)

## Acknowledgements

The <https://twitch.tv/rwxrob> community has been constantly involved
with the development of this project, making suggestions about
everything from my use of `init()`, to the name "bonzai". While all their
contributions are too numerous to name specifically, they 
more than deserve a huge thank you here.

## Legal

Copyright 2022 Robert S. Muhlestein (<mailto:rob@rwx.gg>)  
SPDX-License-Identifier: Apache-2.0

"Bonzai" and "bonzai" are legal trademarks of Robert S. Muhlestein but
can be used freely to refer to the Bonzai™ project
<https://github.com/rwxrob/bonzai> without limitation. To avoid
potential developer confusion, intentionally using these trademarks to
refer to other projects --- free or proprietary --- is prohibited.
