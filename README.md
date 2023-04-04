# Color -> TUI

[![build](https://img.shields.io/drone/build/uttarayan/color-to-tui?server=https%3A%2F%2Fdrone.uttarayan.me)][color-to-tui]
[![build](https://github.com/uttarayan21/color-to-tui/actions/workflows/build.yaml/badge.svg)][mirror]  

Parse HEX colors to [ratatui](https://github.com/tui-rs-revival/ratatui)'s [Rgb](https://docs.rs/ratatui/latest/ratatui/style/enum.Color.html) colors.

## Example

- `#C3F111` -> `Color::Rgb(195,241,17)`
- `#CFB` -> `Color::Rgb(204,255,187)`
- `142` -> `Color::Indexed(142)`  

## Usage

```rust
#[derive(Serialize, Deserialize, PartialEq)]
sruct ColorStruct {
    #[serde(with = "color_to_tui"]
    color: ratatui::style::Color,
    #[serde(with = "color_to_tui::optional"]
    optional_color: Option<ratatui::style::Color>,
}

let color_text =  r###"{ "color" : "#12FC1C", "optional_color" : "123" }"###
let t: ColorStruct = serde_json::from_str::<ColorStruct>(color_text).unwrap();

let c = ColorStruct {
    color: Color::Rgb(18, 252, 28),
    optional_color: Option<Color::Indexed(123)>,
};

assert_eq!(t, c);
```

[color-to-tui]: https://git.uttarayan.me/uttarayan/color-to-tui
[mirror]: https://github.com/uttarayan21/color-to-tui
