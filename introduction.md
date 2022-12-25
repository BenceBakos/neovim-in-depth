# Introduction

## VI/VIM/Neovim is hard
Let's face it, learning VI-like editors is hard. It feels like an enormous amount of time investment for seemingly no big improvement. The rest of this page will contain reasons why it's worth the effort.

## Immortal VI

VI like text editors has a great and rich history, dating back to the 80s unix systems. Some form of it always existed and maintained by a dedicated core community. Most famous example is (VIM)[https://www.vim.org/]. The core concept always remains, consisting of the weirdly effective way of manipulating text plus some degree of customization introduced by vim.
Neovim is a C rewrite of vim, with asynchronous operations, additional features like (LSP)[lsp.md].

VI style text editing is extremely powerful, some form of it will always exist, because those who knows it's value will keep it alive.

## VIM, Neovim improvements

The core advantage of VIM over VI is the customisation. You can manipulate core functionality, the feel, and look of your text editor, thus make a truly unique experience. VIM, and most certainly neovim, is not just about text editing. We can improve developer experience with countless community made plugins, and beat the most advanced IDE's with autocomplete, snippets, debug adapters, refactor, go to definition and much more, while being lightweight, and staying in the same environment we use for other languages as well.

## Lightweight 

When you look at the [unix desktop rice community](https://www.reddit.com/r/unixporn/), you'll find that most of these desktops are installed on crappy old Thinkpads worth a couple bucks. This is a preconception towards [vim enthusiast](https://www.youtube.com/watch?v=9n1dtmzqnCU) as well, and a true one. The current state of software is not great in terms of performance, and that's an understatement. Western world solves this issue by selling more and more powerful computers, but this makes huge inequalities in the society when it comes to using our computers as creative tools, or just using it for day to day tasks. When I open up my old crappy Thinkpad, log into facebook, it's eating up as much memory and CPU time as my system. Horrible bloated slow mess, the kind, a linux enthusiast can't stand, and the same kind you won't find in neovim, because those who use crappy old Thinkpads, are the same developing neovim, and they are very good at keeping it performant, while extending it's functionality.

## This is a linux thing, isn't it?

Yes and No. You can install [Neovim on windows](https://github.com/neovim/neovim/wiki/Installing-Neovim#windows), but that's not it's natural environment.
I've seen many people using it on [Mac](https://github.com/neovim/neovim/wiki/Installing-Neovim#macos--os-x), it is a `*nix` system after all.

Back-end developers love linux because it's reliable, has a ton of essential features and most important of all, they ship software to linux anyways. Using a system similar to one you produce software for, is a great advantage, we can all agree on that. The great thing about vi is it's on every linux box out there by default. When you get used to it's way, and pair it with a good understanding of the command-line, manipulation of those systems becomes a no-brainer.

## Flow

Making conscious decisions is hard. Letting our brain work unconsciously is fast and easy. Software development is about avoiding concious thinking in the future, as much as possible.
[We are designing our systems in such a way, so we can extend it's functionality without modifying existing behaviour.](http://principles-wiki.net/principles:open-closed_principle)
When we can focus on one thing, and progress with foreseeable steps towards our goal, that's flow. We love this kind of feeling, it's addictive, and it's really hard to achieve when our focus is divided, and we have to think about the solution for simple problems. The VI experience is about bringing as much action to the unconscious as possible. The cumbersome series of keystrokes used to edit text in VI can really come from your unconscious mind, and leaves your energy and time for your real job, thinking.
I'll emphasize on it later as well, but forget about your mouse/touchpad. Avoid unpredictable, slow UI, because it brings your actions back to conciousness, and you lose focus.
One great advantage of keys is that you can use them without waiting for feedback, and waiting for feedback divides your attention, and drains your energy, thus makes you less productive.

## Inspiration

Some shows off their cars, we tend to do the same with our neovim configuration, [including me](https://github.com/BenceBakos/comfy-vi-confy).
If you have doubt about what is neovim capable of then look at some examples:

 - [NvChad](https://github.com/NvChad/NvChad)
 - [AstroNvim](https://github.com/AstroNvim/AstroNvim)
 - [CosmicNvim](https://github.com/CosmicNvim/CosmicNvim)

These are the shiny examples, but the configuration best for you, can only come from you. Always keep an eye out for other's favoured setup, and bring the value back to your Neovim experience.

[Continue with basics](basics.md)
