---
title: Text
sidebar_label: Text
---

Text is a control for displaying text.

## Examples

[Live example](https://flet-controls-gallery.fly.dev/displays/text)

### Custom text styles

<img src="/img/docs/controls/text/custom-text-styles.gif" className="screenshot-40"/>

```python
import flet as ft

def main(page: ft.Page):
    page.title = "Text custom styles"
    page.scroll = "adaptive"

    page.add(
        ft.Text("Size 10", size=10),
        ft.Text("Size 30, Italic", size=30, color="pink600", italic=True),
        ft.Text(
            "Size 40, w100",
            size=40,
            color=ft.Colors.WHITE,
            bgcolor=ft.Colors.BLUE_600,
            weight=ft.FontWeight.W_100,
        ),
        ft.Text(
            "Size 50, Normal",
            size=50,
            color=ft.Colors.WHITE,
            bgcolor=ft.Colors.ORANGE_800,
            weight=ft.FontWeight.NORMAL,
        ),
        ft.Text(
            "Size 60, Bold, Italic",
            size=50,
            color=ft.Colors.WHITE,
            bgcolor=ft.Colors.GREEN_700,
            weight=ft.FontWeight.BOLD,
            italic=True,
        ),
        ft.Text("Size 70, w900, selectable", size=70, weight=ft.FontWeight.W_900, selectable=True),
        ft.Text("Limit long text to 1 line with ellipsis", theme_style=ft.TextThemeStyle.HEADLINE_SMALL),
        ft.Text(
            "Proin rutrum, purus sit amet elementum volutpat, nunc lacus vulputate orci, cursus ultrices neque dui quis purus. Ut ultricies purus nec nibh bibendum, eget vestibulum metus various. Duis convallis maximus justo, eu rutrum libero maximus id. Donec ullamcorper arcu in sapien molestie, non pellentesque tellus pellentesque. Nulla nec tristique ex. Maecenas euismod nisl enim, a convallis arcu laoreet at. Ut at tortor finibus, rutrum massa sit amet, pulvinar velit. Phasellus diam lorem, viverra vitae leo vitae, consequat suscipit lorem.",
            max_lines=1,
            overflow=ft.TextOverflow.ELLIPSIS,
        ),
        ft.Text("Limit long text to 2 lines and fading", theme_style=ft.TextThemeStyle.HEADLINE_SMALL),
        ft.Text(
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur quis nibh vitae purus consectetur facilisis sed vitae ipsum. Quisque faucibus sed nulla placerat sagittis. Phasellus condimentum risus vitae nulla vestibulum auctor. Curabitur scelerisque, nibh eget imperdiet consequat, odio ante tempus diam, sed volutpat nisl erat eget turpis. Sed viverra, diam sit amet blandit vulputate, mi tellus dapibus lorem, vitae vehicula diam mauris placerat diam. Morbi sit amet pretium turpis, et consequat ligula. Nulla velit sem, suscipit sit amet dictum non, tincidunt sed nulla. Aenean pellentesque odio porttitor sagittis aliquam. Name various at metus vitae vulputate. Praesent faucibus nibh lorem, eu pretium dolor dictum nec. Phasellus eget dui laoreet, viverra magna vitae, pellentesque diam.",
            max_lines=2,
        ),
        ft.Text("Limit the width and height of long text", theme_style=ft.TextThemeStyle.HEADLINE_SMALL),
        ft.Text(
            "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur quis nibh vitae purus consectetur facilisis sed vitae ipsum. Quisque faucibus sed nulla placerat sagittis. Phasellus condimentum risus vitae nulla vestibulum auctor. Curabitur scelerisque, nibh eget imperdiet consequat, odio ante tempus diam, sed volutpat nisl erat eget turpis. Sed viverra, diam sit amet blandit vulputate, mi tellus dapibus lorem, vitae vehicula diam mauris placerat diam. Morbi sit amet pretium turpis, et consequat ligula. Nulla velit sem, suscipit sit amet dictum non, tincidunt sed nulla. Aenean pellentesque odio porttitor sagittis aliquam. Name various at metus vitae vulputate. Praesent faucibus nibh lorem, eu pretium dolor dictum nec. Phasellus eget dui laoreet, viverra magna vitae, pellentesque diam.",
            width=700,
            height=100,
        ),
    )

ft.app(main)
```

### Pre-defined theme text styles

<img src="/img/docs/controls/text/predefined-text-styles.png" className="screenshot-40" />

```python
import flet as ft

def main(page: ft.Page):
    page.title = "Text theme styles"
    page.scroll = "adaptive"

    page.add(
        ft.Text("Display Large", theme_style=ft.TextThemeStyle.DISPLAY_LARGE),
        ft.Text("Display Medium", theme_style=ft.TextThemeStyle.DISPLAY_MEDIUM),
        ft.Text("Display Small", theme_style=ft.TextThemeStyle.DISPLAY_SMALL),
        ft.Text("Headline Large", theme_style=ft.TextThemeStyle.HEADLINE_LARGE),
        ft.Text("Headline Medium", theme_style=ft.TextThemeStyle.HEADLINE_MEDIUM),
        ft.Text("Headline Small", theme_style=ft.TextThemeStyle.HEADLINE_SMALL),
        ft.Text("Title Large", theme_style=ft.TextThemeStyle.TITLE_LARGE),
        ft.Text("Title Medium", theme_style=ft.TextThemeStyle.TITLE_MEDIUM),
        ft.Text("Title Small", theme_style=ft.TextThemeStyle.TITLE_SMALL),
        ft.Text("Label Large", theme_style=ft.TextThemeStyle.LABEL_LARGE),
        ft.Text("Label Medium", theme_style=ft.TextThemeStyle.LABEL_MEDIUM),
        ft.Text("Label Small", theme_style=ft.TextThemeStyle.LABEL_SMALL),
        ft.Text("Body Large", theme_style=ft.TextThemeStyle.BODY_LARGE),
        ft.Text("Body Medium", theme_style=ft.TextThemeStyle.BODY_MEDIUM),
        ft.Text("Body Small", theme_style=ft.TextThemeStyle.BODY_SMALL),
    )

ft.app(main)
```

### Font with variable weight

<img src="/img/docs/controls/text/variable-weight-font.gif" className="screenshot-50" />

```python
import flet as ft

def main(page: ft.Page):
    page.fonts = {
        "RobotoSlab": "https://github.com/google/fonts/raw/main/apache/robotoslab/RobotoSlab%5Bwght%5D.ttf"
    }

    t = ft.Text(
        "This is rendered with Roboto Slab",
        size=30,
        font_family="RobotoSlab",
        weight=ft.FontWeight.W_100,
    )

    def width_changed(e):
        t.weight = f"w{int(e.control.value)}"
        t.update()

    page.add(
        t,
        ft.Slider(
            min=100,
            max=900,
            divisions=8,
            label="{value}",
            width=500,
            on_change=width_changed,
        ),
    )

ft.app(main)
```

### Rich text basics

<img src="/img/docs/controls/text/richtext.png" className="screenshot-70" />

```python
import flet as ft

def main(page: ft.Page):
    page.add(
        ft.Text("Plain text with default style"),
        ft.Text(
            "Some text",
            size=30,
            spans=[
                ft.TextSpan(
                    "here goes italic",
                    ft.TextStyle(italic=True, size=20, color=ft.Colors.GREEN),
                    spans=[
                        ft.TextSpan(
                            "bold and italic",
                            ft.TextStyle(weight=ft.FontWeight.BOLD),
                        ),
                        ft.TextSpan(
                            "just italic",
                            spans=[
                                ft.TextSpan("smaller italic", ft.TextStyle(size=15))
                            ],
                        ),
                    ],
                )
            ],
        ),
        ft.Text(
            disabled=False,
            spans=[
                ft.TextSpan(
                    "underlined and clickable",
                    ft.TextStyle(decoration=ft.TextDecoration.UNDERLINE),
                    on_click=lambda e: print(f"Clicked span: {e.control.uid}"),
                    on_enter=lambda e: print(f"Entered span: {e.control.uid}"),
                    on_exit=lambda e: print(f"Exited span: {e.control.uid}"),
                ),
                ft.TextSpan(" "),
                ft.TextSpan(
                    "underlined red wavy",
                    ft.TextStyle(
                        decoration=ft.TextDecoration.UNDERLINE,
                        decoration_color=ft.Colors.RED,
                        decoration_style=ft.TextDecorationStyle.WAVY,
                    ),
                    on_enter=lambda e: print(f"Entered span: {e.control.uid}"),
                    on_exit=lambda e: print(f"Exited span: {e.control.uid}"),
                ),
                ft.TextSpan(" "),
                ft.TextSpan(
                    "overlined blue",
                    ft.TextStyle(
                        decoration=ft.TextDecoration.OVERLINE, decoration_color="blue"
                    ),
                ),
                ft.TextSpan(" "),
                ft.TextSpan(
                    "overlined and underlined",
                    ft.TextStyle(
                        decoration=ft.TextDecoration.OVERLINE
                        | ft.TextDecoration.UNDERLINE
                    ),
                ),
                ft.TextSpan(" "),
                ft.TextSpan(
                    "line through thick",
                    ft.TextStyle(
                        decoration=ft.TextDecoration.LINE_THROUGH,
                        decoration_thickness=3,
                    ),
                ),
            ],
        ),
    )

    def highlight_link(e):
        e.control.style.color = ft.Colors.BLUE
        e.control.update()

    def unhighlight_link(e):
        e.control.style.color = None
        e.control.update()

    page.add(
        ft.Text(
            disabled=False,
            spans=[
                ft.TextSpan("AwesomeApp 1.0 "),
                ft.TextSpan(
                    "Visit our website",
                    ft.TextStyle(decoration=ft.TextDecoration.UNDERLINE),
                    url="https://google.com",
                    on_enter=highlight_link,
                    on_exit=unhighlight_link,
                ),
                ft.TextSpan(" All rights reserved. "),
                ft.TextSpan(
                    "Documentation",
                    ft.TextStyle(decoration=ft.TextDecoration.UNDERLINE),
                    url="https://google.com",
                    on_enter=highlight_link,
                    on_exit=unhighlight_link,
                ),
            ],
        ),
    )

ft.app(main)
```

### Rich text with borders and stroke

<img src="/img/docs/controls/text/richtext-borders-stroke.png" className="screenshot-50" />

```python
import flet as ft

def main(page: ft.Page):
    page.add(
        ft.Stack(
            [
                ft.Text(
                    spans=[
                        ft.TextSpan(
                            "Greetings, planet!",
                            ft.TextStyle(
                                size=40,
                                weight=ft.FontWeight.BOLD,
                                foreground=ft.Paint(
                                    color=ft.Colors.BLUE_700,
                                    stroke_width=6,
                                    stroke_join=ft.StrokeJoin.ROUND,
                                    style=ft.PaintingStyle.STROKE,
                                ),
                            ),
                        ),
                    ],
                ),
                ft.Text(
                    spans=[
                        ft.TextSpan(
                            "Greetings, planet!",
                            ft.TextStyle(
                                size=40,
                                weight=ft.FontWeight.BOLD,
                                color=ft.Colors.GREY_300,
                            ),
                        ),
                    ],
                ),
            ]
        )
    )

ft.app(main)
```

### Rich text with gradient

<img src="/img/docs/controls/text/richtext-gradient.png" className="screenshot-50" />

```python
import flet as ft

def main(page: ft.Page):
    page.add(
        ft.Text(
            spans=[
                ft.TextSpan(
                    "Greetings, planet!",
                    ft.TextStyle(
                        size=40,
                        weight=ft.FontWeight.BOLD,
                        foreground=ft.Paint(
                            gradient=ft.PaintLinearGradient(
                                (0, 20), (150, 20), [ft.Colors.RED, ft.Colors.YELLOW]
                            )
                        ),
                    ),
                ),
            ],
        )
    )

ft.app(main)
```

## Properties

### `bgcolor`

Text background [color](/docs/reference/colors).

### `color`

Text foreground [color](/docs/reference/colors).

### `font_family`

System or custom font family to render text with. See [`Fonts`](/docs/controls/page#fonts) cookbook guide for instructions on how to import and use custom fonts in your application.

### `italic`

`True` to use italic typeface.

Value is of type `bool` and defaults to `False`.

### `max_lines`

An optional maximum number of lines for the text to span, wrapping if necessary. If the text exceeds the given number of lines, it will be truncated according to `overflow`.

If this is 1, text will not wrap. Otherwise, text will be wrapped at the edge of the box.

### `no_wrap`

If `False` (default) the text should break at soft line breaks.

If `True`, the glyphs in the text will be positioned as if there was unlimited horizontal space.

Value is of type `bool` and defaults to `False`.

### `overflow`

Controls how text overflows.

Value is of type [`TextOverflow`](/docs/reference/types/textoverflow) and defaults to `TextOverflow.FADE`.

### `rtl`

`True` to set text direction to right-to-left.

Defaults to `False`.

### `selectable`

Whether the text should be selectable.

Defaults to `False`.

### `semantics_label`

An alternative semantics label for this text.

If present, the semantics of this control will contain this value instead of the actual text. This will overwrite any of the `TextSpan.semantics_label`s.

This is useful for replacing abbreviations or shorthands with the full text value:

Value is of type `str`.

```python
ft.Text("$$", semantics_label="Double dollars")
```

### `size`

Text size in virtual pixels.

Value is of type `OptionalNumber` and defaults to `14`.

### `spans`

The list of [`TextSpan`](/docs/reference/types/textspan) objects to build a rich text paragraph.

### `style`

The text's style.

Value is of type [`TextStyle`](/docs/reference/types/textstyle).

### `text_align`

Text horizontal align.

Value is of type [`TextAlign`](/docs/reference/types/textalign) and defaults to `TextAlign.LEFT`.

### `theme_style`

Pre-defined text style.

Value is of type [`TextThemeStyle`](/docs/reference/types/textthemestyle).

### `value`

The text displayed.

Value is of type `str`.

### `weight`

Font weight.

Value is of type [`FontWeight`](/docs/reference/types/fontweight) and defaults to `FontWeight.NORMAL`.

