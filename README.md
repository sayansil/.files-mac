# Configure yabai in macOS

## Pre-requisites

- Install [jq](https://github.com/stedolan/jq) to parse json in bash scripts

```shell
brew install jq
```

- Open *System Preferences > Accessibility > Display* and check the *Reduce motion* option for smoother switch between workspaces.

![Settings page](https://www.linkpicture.com/q/Screenshot-2022-03-10-at-10.07.10-PM.png)

- Open *System Preferences > Mission Control*

  - Uncheck the *Automatically rearrange Spaces based on most recent use* option

  - Check the *Displays have separate Spaces* option

![Settings page](https://www.linkpicture.com/q/Screenshot-2022-03-11-at-12.09.48-AM.png)

## Setup `hyper` key (⌃ ⌥ ⇧ ⌘)

- Install [Karabiner](https://karabiner-elements.pqrs.org/)

```shell
brew install --cask karabiner-elements
```

- This installs two applications: **Karabiner-Elements** and **Karabiner-EventViewer**

- Open *System Preferences > Security & Privacy > Privacy > Input Monitoring*

- Add the following to the *Input Monitoring* section and enable them.

    a) **Karabiner-Elements** *(location: Applications)*

    b) **Karabiner-EventViewer** *(location: Applications)*

    c) **karabiner_observer** *(location: /Library/Application Support/org.pqrs/Karabiner-Elements/bin)*

    d) **karabiner_grabber** *(location: /Library/Application Support/org.pqrs/Karabiner-Elements/bin)*

![Settings Page](https://www.linkpicture.com/q/krabby.png)

- Open **Karabiner-EventViewer** application and check for keystrokes being registered correctly.

- Open **Karabiner-Elements** app and then allow `Karabringer-VirtualHIDDevice-Manager` to load from *System Preferences > General* in your Mac.

- Restart **Karabiner-Elements** app.

- In *Function Keys* tab, reset actions of all Function keys to default values.

- In *Devices* tab, check only the Mac keyboard. Uncheck rest of the devices. Keep the *Manipulate LED* option checked.

- In *Misc* tab, uncheck *Show icon in Menu bar* option.

- To import the `hyper` key custom modification, open [this link](https://ke-complex-modifications.pqrs.org/#hyper_key) and click on **Import**.

- Import just the `Caps Lock → Hyper Key (⌃⌥⇧⌘) (Caps Lock if alone)` modification.

- Close **Karabiner-Elements** and open **Karabiner-EventViewer**.

- Check if just pressing `CAPS LOCK` triggers the usual function and holding it with any key triggers `hyper + key`.

---

## Setup `skhd` (Keyboard shortcuts)

- Install [skhd](https://github.com/koekeishiya/skhd)

```shell
brew install koekeishiya/formulae/skhd
```

- Create new config file for skhd

```shell
touch ~/.config/skhd/skhdrc
chmod +x ~/.config/skhd/skhdrc
```

- Populate the `skhdrc` file with your config. Example [here](https://github.com/koekeishiya/skhd/blob/master/examples/skhdrc).

- Make `skhd` start everytime on startup

```shell
brew services start skhd
```

---

## Setup `limelight` (Highlight focused window)

- Make sure to kill any existing instances of previously installed limelight still running.

```shell
killall limelight &> /dev/null
limelight &> /dev/null &
```

- Clone and build [limelight](https://github.com/koekeishiya/limelight)

```shell
git clone https://github.com/koekeishiya/limelight.git
cd limelight
make
```

- Copy `bin/limelight` to `/usr/local/bin` or any other place which is included in PATH

```shell
cp bin/limelight /usr/local/bin
```

OR create a symlink of `bin/limelight` there.

```shell
ln -s bin/limelight /usr/local/bin/limelight
```

- Create config file. Example [here](https://github.com/sayansil/.files-mac/blob/main/config/limelight/limelightrc).

```shell
touch ~/.config/limelight/limelightrc
chmod +x ~/.config/limelight/limelightrc
```

---

## Setup `yabai` (WM)

- Install [yabai](https://github.com/koekeishiya/yabai)

```shell
brew install koekeishiya/formulae/yabai
```

- Create config file. Example [here](https://github.com/koekeishiya/yabai/blob/master/examples/yabairc).

```shell
touch ~/.config/yabai/yabairc
chmod +x ~/.config/yabai/yabairc
```

- Make `yabai` start everytime on startup

```shell
brew services start yabai
```
