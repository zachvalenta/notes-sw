# ⛩️

## 参考

🗄
* `golang.md` CLI
* `shell.md` design

GUI
* _Gooey_: https://github.com/chriskiehl/Gooey
* _Kivy_: https://github.com/kivy/kivy
* _pyautogui_: control mouse/keyboard https://github.com/asweigart/pyautogui
* _pyqt_: https://build-system.fman.io/pyqt5-tutorial
* _PySimpleGUI_:  https://github.com/PySimpleGUI/PySimpleGUI
* _tkinter_: https://www.youtube.com/watch?v=xqDonHEYPgA https://pywebview.flowrl.com/

## 进步

# 🖱️ CLICK

📜 https://click.palletsprojects.com/en/8.1.x

### basic

```python
@click.group()
def cli():
    pass
@cli.command()
def command_one():
    logger.info("this is command one!")
if __name__ == "__main__":
    cli()
```
```sh
python $SCRIPT command-one
```

### args

```sh
make crud join=join.csv vend=aaon.csv
```
```Makefile
crud:
	python mapper.py $(join) $(vend)
```
```python
@click.command()
@click.argument("join_file", type=click.Path(exists=True))
@click.argument("vendor_file", type=click.Path(exists=True))
def process_files(join_file, vendor_file):
```

### default cmd

```python
# SANS DATACLASS
@click.group(invoke_without_command=True)
@click.pass_context
def cli(ctx):
    if ctx.invoked_subcommand is None:
        ctx.invoke(command_one)
@cli.command()
def command_one():
    logger.info("this is command one!")
if __name__ == "__main__":
    cli()
# WITH DATACLASS
@dataclass
class Cmd:
    @click.group(invoke_without_command=True)
    @click.pass_context
    def cli(ctx):
        if ctx.invoked_subcommand is None:
            ctx.invoke(Cmd.command_one)
    @cli.command()
    def command_one():
        logger.info("this is command one!")
if __name__ == '__main__':
    Cmd.cli()
```
```sh
python $SCRIPT
```

---

* can encapsulate in dataclass
```python
@dataclass
class Pipeline:
    @click.group()
    def cli():
        pass
    @cli.command()
    def command_one():
        Util.strip_metadata()
if __name__ == '__main__':
    Pipeline.cli()
```

* `python script.py`
```python
#!/usr/bin/env python
import click

@click.command()
def main():
    print("hello world")

if __name__ == "__main__":
    main()
```

command + arg
```python
# run: python script.py hello alice

@click.group()
def cli():
    pass

@cli.command()
@click.argument("person")
def hello(person):
    print(f"hi, {person}")

@cli.command()
@click.argument("person")
def goodbye(person):
    print(f"goodbye, {person}")
```

---

* port Click app to TUI https://github.com/Textualize/trogon

ALTERNATIVES
* `sys.argv`
* optparse
* docopt
* https://github.com/tiangolo/typer https://rahulpai.co.uk/smart-clis-with-typer.html
* interactive https://github.com/Aperocky/replbuilder
* Rust https://saadmk11.github.io/blog/posts/build-python-cli-tool-with-rust/
* CLI from obj: https://github.com/google/python-fire https://github.com/chriskiehl/Gooey https://github.com/BstLabs/py-dynacli

INTERPRETER / SHEBANG
```sh
# https://realpython.com/run-python-scripts/#using-the-script-filename
#!/usr/bin/python --> explicit path
#!/usr/bin/env python --> use whatever python on $PATH
```

ARGPARSE
* rich for output https://github.com/hamdanal/rich-argparse
* testing: https://github.com/dbader/photosorter/blob/master/test_sorter.py https://www.youtube.com/watch?v=ApTZib0L2X8 4:00
* `description`: one-liner on purpose of CLI http://dustinrcollins.com/testing-python-command-line-apps
* `action=store_true`: boolean https://stackoverflow.com/a/15008806/6813490 https://stackoverflow.com/a/36710639/6813490
* `metavar=''`: avoid weird upppercasing https://docs.python.org/3/library/argparse.html#metavar
* scaffold
```python
def parse():
    parser = ArgumentParser()
    parser.add_argument("-f", "--file", help="file")
    parser.add_argument("-s", "--start", help="start trim")
    parser.add_argument("-e", "--end", help="end trim")
    if len(argv) == 1:
        parser.print_help()
        exit()
    return parser.parse_args()

args = parse()
main(file=args.file, start=args.start, end=args.end)
```

MORE CLICK
* args vs. options https://click.palletsprojects.com/en/8.1.x/parameters/
* types: str, int https://click.palletsprojects.com/en/8.1.x/parameters/#parameter-types
> I'm not using these semantically, using options in lieu of args bc options have better syntax on command invocation
```python
# ARGS: python path/to/script.py path/to/file
@click.command()
@click.argument("in-file", type=click.Path(exists=True))
def main(in_file):
    """input file"""  # https://click.palletsprojects.com/en/8.1.x/documentation/

# OPTIONS: python path/to/script.py -in-file path/to/file
@click.command()
@click.option("-in-file", required=True, type=str, help="input file")
def main(in_file):
```
* read from anywhere, write to local dir
```python
# run: python script.py -in_path path/to/file.txt -out_file new_file.txt
@click.command()
@click.option("-in_path", required=True, type=str, help="path to input file")
@click.option("-out_file", required=True, type=str, help="output filename")
def main(in_path, out_file):
    path_input = os.path.normpath(in_path)
    path_output = os.path.join(os.getcwd(), out_file)
    with open(path_output, mode="w") as csv_out:
        with open(path_input, mode="r") as csv_in:
```

# 🔣 INPUT

🗄 `security.md` sanitization

```python
ur_in = input()
```
* Textual https://github.com/darrenburns/textual-autocomplete
* _prompt-toolkit_: used by pgcli, http-prompt https://github.com/j-bennet/wharfee/blob/master/setup.py https://github.com/wasi-master/fastero

## 🚅 bullet

---

* _bullet_: https://github.com/Mckinsey666/bullet Golang alternative https://github.com/charmbracelet/huh
* repos https://github.com/zachvalenta/news https://github.com/zachvalenta/capp-prod-cat/blob/link-nodes/tree_viz.py 🗄️ `git.md` Github / search
* control flow https://github.com/shkey/killurp/blob/141d411d353ab46edf362ff6a33bfe9c5a5ad211/killurp.py#L8 https://github.com/chroma-core/chroma-migrate/blob/2a6e61ee7f2d717281075512b308c40616033189/chroma_migrate/cli.py#L2

## questionary

* _questionary_: https://github.com/tmbo/questionary https://calmcode.io/shorts/questionary

# 📺 TUI

🗄️
* `ml.md` clients > Elia
* `os/tools.md` browsr

TUI
* Rust renaissance https://www.youtube.com/watch?v=OxfxkWoHhxM
* https://news.ycombinator.com/item?id=40273177
* _curses_: UNIX https://docs.python.org/3/howto/curses.html https://github.com/cmus/cmus 
* ncurses
* https://news.ycombinator.com/item?id=37418424
* TUI for bash https://github.com/charmbracelet/gum
* design https://www.micahlerner.com/2021/07/14/unix-shell-programming-the-next-50-years.html 🗣 Dan Luu https://borretti.me/article/shells-are-two-things extensions https://github.com/dotenvx/dotenvx/pull/426

ALTERNATIVES
> Textual inherently slow? Both browsr and elia crawl on open. Find Golang-like alternative
> prefer the way Golang/Rust TUI libs look (gocui, ratatui, tokie) https://github.com/charmbracelet/bubbles https://github.com/alexpasmantier/television
* _blessed_: https://github.com/jquast/blessed
* _asciimatics_: https://github.com/peterbrittain/asciimatics
* _urwid_: used by pudb, Zulip http://urwid.org/ https://github.com/zulip/zulip-terminal/blob/main/zulipterminal/ui_tools/boxes.py
* _pytermgui_: https://github.com/bczsalba/pytermgui

---

## 🦄 Charm

🔗 https://charm.sh/

* _Bubbles_: standalone UI components from Bubbletea https://github.com/charmbracelet/bubbles
* text input (does it support readline?) https://github.com/charmbracelet/bubbles?tab=readme-ov-file#text-input
* _Bubbletea_: TUI framework https://github.com/charmbracelet/bubbletea https://github.com/charmbracelet/bubbletea#bubble-tea-in-the-wild
* _huh_: forms; used in gum https://github.com/charmbracelet/huh
* _log_: structured logs, used in gum https://github.com/charmbracelet/log https://github.com/charmbracelet/gum#log

---

📹 https://www.youtube.com/watch?v=_gzypL-Qv-g

* _Bubble Tea_: inspired by Elm? https://github.com/charmbracelet/bubbletea
* tutorials https://leg100.github.io/en/posts/building-bubbletea-programs/ https://www.youtube.com/watch?v=ERaZi0YvBRs
* components https://github.com/charmbracelet/bubbles 

## ratatui

## Textual

HOWTO
* debug https://www.pythonpapers.com/p/how-to-debug-your-textual-application
* publish to web https://github.com/Textualize/textual-web
* file tree https://github.com/willmcgugan/terminal-tree
* run examples
```sh
python -m pip install --user textual
cd /Users/zvalenta/Desktop/textual/examples
python json_tree.py
```

PROJECTS THAT USE
* https://github.com/thetacom/hexabyte
* Harlequin (UI almost as slick as lazydocker)

---

* close to CSS, Tailwind https://calmcode.io/labs/tuilwind-css
* https://realpython.com/contact-book-python-textual/
* functionality: tables, color, layout
* _Textual_: complaints https://news.ycombinator.com/item?id=35123383 animation https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#demonstrating-animation dropdown https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#dropdown-autocompletion-menu file manager https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#a-file-manager-powered-by-textual graphics https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#pixel-art layout https://textual.textualize.io/blog/2022/12/11/version-060/#placeholder tabs https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#tabs-with-animated-underline testing https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#developer-console https://textual.textualize.io/blog/2022/12/20/a-year-of-building-for-the-terminal/#snapshot-testing-for-terminal-apps example https://github.com/learnbyexample/TUI-apps/tree/main/CLI-Exercises https://www.blog.pythonlibrary.org/2024/02/06/creating-a-modal-dialog-for-your-tuis-in-textual/

# 🟨 ZA

## assorted Golang

---

* animation https://github.com/charmbracelet/harmonica
* frameworks https://github.com/noahgorstein/jqp https://www.youtube.com/watch?v=ZA93qgdLUzM https://github.com/rivo/tview/ https://github.com/jroimartin/gocui 
* color https://github.com/fatih/color
* tables https://github.com/jedib0t/go-pretty
* Markdown render https://github.com/charmbracelet/glamour https://miller.readthedocs.io/en/latest/file-formats/#markdown-tabular
* prompt https://github.com/manifoldco/promptui
* styling https://github.com/charmbracelet/lipgloss https://github.com/pterm/pterm/

---

* testing, golden files https://changelog.com/gotime/337
* https://www.dolthub.com/blog/2023-03-29-interactive-shell-golang/

* https://clig.dev/ https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46 https://www.youtube.com/watch?v=eMz0vni6PAw https://eryb.space/2020/05/27/diving-into-go-by-building-a-cli-application.html https://blog.carlmjohnson.net/post/2020/go-cli-how-to-and-advice/ email author -> 艘 'Golang article typo'
```sh
├── main.foo  # single line returning exit code from internals https://blog.carlmjohnson.net/post/2020/go-cli-how-to-and-advice/
│   └── file_1.txt
│   └── file_2.txt
```
* binaries for multiple architectures https://www.thoughtworks.com/radar/tools?blipid=202203018 https://github.com/goreleaser/goreleaser
* https://towardsdatascience.com/how-to-create-a-cli-in-golang-with-cobra-d729641c717 https://www.twilio.com/blog/use-cobra-build-go-powered-clis
* _stdlib_:  https://media.pragprog.com/titles/rggo/first.pdf approach 1 https://eryb.space/2020/05/27/diving-into-go-by-building-a-cli-application.html https://github.com/erybz/go-grab-xkcd approach 2 https://blog.carlmjohnson.net/post/2020/go-cli-how-to-and-advice/ https://github.com/carlmjohnson/go-grab-xkcd `flags` not good? https://golang.org/pkg/flag/ https://news.ycombinator.com/item?id=23319770 https://news.ycombinator.com/item?id=23321901
* _Cobra/Viper_: Hugo, Kubernetes https://news.ycombinator.com/item?id=23319172 scaffold https://github.com/spf13/cobra/blob/master/cobra/README.md module support https://github.com/spf13/cobra/issues/1054 https://github.com/spf13/cobra/issues/795 https://github.com/spf13/cobra/pull/817 https://qua.name/antolius/making-a-testable-cobra-cli-app https://www.youtube.com/watch?v=44MMeT39eG4
* _cli_: https://github.com/urfave/cli https://github.com/ayoisaiah/goname/blob/master/cmd/goname/main.go https://news.ycombinator.com/item?id=23321576
* _alternatives_: terminal GUI https://github.com/rivo/tview https://www.youtube.com/watch?v=aiWOTYiIzyE other options https://go.dev/solutions/clis/ https://github.com/jessevdk/go-flags https://github.com/jaffee/commandeer
* _interactive prompt_: https://github.com/AlecAivazis/survey
* output https://github.com/nikolaydubina/calendarheatmap https://xkcd.com/1138/ https://github.com/vbauerster/mpb https://github.com/cirruslabs/echelon https://github.com/gookit/color/ https://github.com/Delta456/box-cli-maker colors https://github.com/muesli/termenv

- [ ] packaging - recreate Cobra scaffold `golang/packaging`

* ✅ try to run app
* snapshot (env, fs, previous notes at bottom of file, Makefile)
* cp project somewhere else, rm deps (clean --modcache), 'clone', run
* cp project somewhere else, rm deps (not folders), 'clone', run
* cp project somewhere else, rm deps (folders), 'clone', run
* push to GH, rm deps (clean --modcache), clone, run
* push to GH, rm deps (not folder), clone, run
* push to GH, rm deps (folders), clone, run
* basic project w/out deps https://golang.org/doc/code.html
* get set up on work machine

## design

📜 http://gnu.ist.utl.pt/prep/standards/html_node/Command_002dLine-Interfaces.html

24.12.11
* positional for one|two obvious args
* keyword for options

---

https://jvns.ca/blog/2024/11/26/terminal-rules/ https://news.ycombinator.com/item?id=42401011
https://danluu.com/cli-complexity/

CLI IMPL LANGUAGE
> use Rust for CLI and Python for business logic? https://github.com/chubin/wttr.in
* tracking user info https://www.visidata.org/blog/2021/usage-graphs/
> build modern CLI applications without worrying about user accounts, data storage and encryption https://github.com/charmbracelet/charm#charm-kv
* fuzzy find https://github.com/denisidoro/navi
* C: ✅ fast ❌ development speed
* Nim: ✅ distribution ❌ maturity https://ssalewski.de/nimprogramming.html
* Python: ✅ exploratory ❌ distribution
* Go: ✅ distribution, fast startup https://news.ycombinator.com/item?id=23319684 ❌ stdlib lib lib not good
* Rust: ✅ speed, Clap library https://news.ycombinator.com/item?id=23320411 better for cross platform https://cuchi.me/posts/go-vs-rust ❌ language itself

OPTIONS 🔗 http://www.catb.org/~esr/writings/taoup/html/ch10s05.html
* _short option_: single dash prefix + single letter e.g. `-y`
* _option set_: n short options e.g. `-baz` = `-b`, `a`, `z`
* _long option_: double dash prefix + word e.g. `--foo-bar`
* options with a value are separated by their option by a space or an `=`
* `--`: ends option processing.

INPUT https://news.ycombinator.com/item?id=31293032
* https://nullprogram.com/blog/2020/08/01/
* _flag_: hyphen e.g. `cmd --from here --to there`
* letter (`-h`) word (`--help`) https://www.youtube.com/watch?v=FOQHGz__OLs
* _arg_: no hypen `cmd here there`; less clear than flags bc have to remember which is src and which is target https://medium.com/@jdxcode/12-factor-cli-apps-dd3c227a0e46

## 🍬 gum

📜 https://github.com/charmbracelet/gum
💻
* log https://github.com/zachvalenta/capp-crudite
* filter https://github.com/zachvalenta/bin-mini23/blob/main/xmp
* input https://github.com/zachvalenta/capp-denv-bin

* tldr: components for Bash scripts https://github.com/charmbracelet/gum/blob/main/examples/test.sh
* use in Python https://github.com/charmbracelet/gum/blob/main/examples/gum.py
* welcome msg https://github.com/charmbracelet/gum#join
```sh
gum style --foreground 212 --border-foreground 212 --border double \
	--align center --width 50 --margin "1 2" --padding "2 2" 'generate' 'dataset' 'for' 'crudite'
```

## 💰 rich

📜 https://github.com/Textualize/rich
💻
* https://github.com/zachvalenta/dotfiles-mini23/blob/main/python/python_startup.py
* https://github.com/zachvalenta/learn-econ-with-python

* html https://github.com/willmcgugan/willmcgugan/blob/master/willmcgugan.py
* to try: repr for obj https://rich.readthedocs.io/en/latest/pretty.html#rich-repr-protocol
https://rich.readthedocs.io/en/latest/introduction.html#ipython-extension
```python
from rich import print as rp  # print
from rich import pretty; pretty.install()  # default to Rich print in REPL
from rich import inspect
inspect(superhero, methods=True)  # more limited version of stdlib inspect

# EXCEPTIONS
from rich.console import Console
console = Console()
from rich.traceback import install
install(show_locals=True)

raise RuntimeError("hey there")  # normal output (contra examples)?

try:  # Rich output
    do_something()
except Exception:
    console.print_exception(show_locals=True)
```

OUTPUT
* animation 🎯 https://github.com/ChrisBuilds/terminaltexteffects https://realpython.com/python-rich-package/
* colors https://github.com/timofurrer/colorful https://github.com/erikrose/blessings
* syntax highlighting https://github.com/pygments/pygments
* tables https://github.com/astanin/python-tabulate https://realpython.com/python-rich-package/
```txt
dim - Dimmed text
reverse - Reverse colors
blink - Blinking text
strike - Strikethrough
italic - Italicized text
```