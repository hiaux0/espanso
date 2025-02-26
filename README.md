![espanso](images/logo_extended.png)

> A cross-platform Text Expander written in Rust

![GitHub release (latest by date)](https://img.shields.io/github/v/release/espanso/espanso)
![Language](https://img.shields.io/badge/language-rust-orange)
![Platforms](https://img.shields.io/badge/platforms-Windows%2C%20macOS%20and%20Linux-blue)
![License](https://img.shields.io/github/license/espanso/espanso)

![example](images/example.gif)

Visit the [espanso website](https://espanso.org).

#### What is a Text Expander?

A *text expander* is a program that detects when you type
a specific **keyword** and replaces it with **something else**.
This is useful in many ways:

* **Save a lot of typing**, expanding common sentences.
* Create **system-wide** code snippets.
* Execute **custom scripts**
* Use **emojis** like a pro.

___

## Key Features

* Works on **Windows**, **macOS** and **Linux**
* Works with almost **any program**
* Works with **Emojis** 😄
* Works with **Images**
* Includes a powerful **Search Bar** 🔎
* **Date** expansion support
* **Custom scripts** support
* **Shell commands** support
* **App-specific** configurations
* Support [Forms](https://espanso.org/docs/matches/forms/)
* Expandable with **packages**
* Built-in **package manager** for [espanso hub](https://hub.espanso.org/)
* File based configuration
* Support Regex triggers
* Experimental Wayland support

## Get Started

Visit the [official documentation](https://espanso.org/docs/).

## Support

If you need some help to setup espanso, want to ask a question or simply get involved
in the community, [Join the official Subreddit](https://www.reddit.com/r/espanso/)! :)

## Donations

espanso is a free, open source software developed in my (little) spare time.
If you liked the project and would like to support further development,
please consider making a small donation, it really helps :)

[![Donate with PayPal](images/donate.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=FHNLR5DRS267E&source=url)

## Contributors

Many people helped the project along the way, thank you to all of you!

[![Image](https://contrib.rocks/image?repo=espanso/espanso)](https://github.com/espanso/espanso/graphs/contributors)

## Remarks

* Thanks to [libxdo](https://github.com/jordansissel/xdotool) and [xclip](https://github.com/astrand/xclip), used to implement the Linux port.
* Thanks to [libxkbcommon](https://xkbcommon.org/) and [wl-clipboard](https://github.com/bugaevc/wl-clipboard), used to implement the Wayland port.
* Thanks to [wxWidgets](https://www.wxwidgets.org/) for providing a powerful cross-platform GUI library.

## License

espanso was created by [Federico Terzi](http://federicoterzi.com)
and is licensed under the [GPL-3.0 license](/LICENSE).

## Text Injection Functionality

The text injection functionality in espanso is responsible for injecting text into the user's input field. This functionality is implemented using the `TextInjectExecutor` struct and the `TextInjector` trait.

### TextInjectExecutor

The `TextInjectExecutor` struct is responsible for injecting text into the user's input field. It uses two injectors: `event_injector` and `clipboard_injector`.

Relevant file: `espanso-engine/src/dispatch/executor/text_inject.rs`

### TextInjector Trait

The `TextInjector` trait defines the `inject_text` method, which is used to inject text.

Relevant file: `espanso-engine/src/dispatch/executor/text_inject.rs`

### ClipboardInjector and EventInjector

The `ClipboardInjector` and `EventInjector` structs implement the `TextInjector` trait. They are responsible for injecting text using the clipboard and event methods, respectively.

Relevant files:
- `espanso/src/cli/worker/engine/dispatch/executor/clipboard_injector.rs`
- `espanso/src/cli/worker/engine/dispatch/executor/event_injector.rs`

### Relevant Files and Their Roles

- `espanso-engine/src/dispatch/executor/text_inject.rs`: Contains the `TextInjectExecutor` struct and the `TextInjector` trait.
- `espanso-engine/src/dispatch/executor/mod.rs`: Re-exports the `TextInjector` trait.
- `espanso-engine/src/dispatch/mod.rs`: Re-exports the `text_inject` module.
- `espanso/src/cli/worker/engine/dispatch/executor/mod.rs`: Contains the `InjectParamsProvider` trait, which provides parameters for text injection.
- `espanso/src/cli/worker/engine/dispatch/executor/clipboard_injector.rs`: Contains the `ClipboardInjector` struct, which implements the `TextInjector` trait.
- `espanso/src/cli/worker/engine/dispatch/executor/event_injector.rs`: Contains the `EventInjector` struct, which implements the `TextInjector` trait.
- `espanso/src/cli/worker/engine/dispatch/mod.rs`: Re-exports the `executor` module.
- `espanso/src/cli/worker/engine/mod.rs`: Re-exports the `dispatch` module.
- `espanso/src/cli/worker/mod.rs`: Re-exports the `engine` module.
- `espanso/src/main.rs`: Initializes and runs the application, which includes the text injection functionality.
