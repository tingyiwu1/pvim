# Portable-vim

pvim, AKA seanvim, is an AllInOne-directory Neovim wrapper.

pvim will download the latest Neovim appimage and contain all data, state, and
plugins to within the download directory. This should work on any linux computer
that can run an appimage, and can be downloaded from any computer that has git
and curl.

## Installation

Clone pvim to whatever location you wish then add it to your path.

```sh
cd
git clone git@github.com:tingyiwu1/pvim.git
```

Copy or symlink your neovim config to the default nvim config location.
```sh
git clone git@github.com:tingyiwu1/dotfiles.git

# Manual symlink
ln -sr dotfiles/nvim/.config/nvim .config/nvim
# -- OR --
# Using stow
cd dotfiles
stow nvim
```
Symlink pvim executable to `~/bin`
```sh
cd
mkdir -p ~/bin
ln -sr pvim/pvim ~/bin/nvim
```

You may need to add `~/bin` to PATH if it's not already there.

## Finding Neovim

On running `pvim`, it will first look for the Neovim appimage in the pvim
directory, if it is not there it will check if `nvim` is in path, if neither are
available it will download the latest appimage.  
If you would rather use the appimage than the current installed version, you can
force it's use with `-f` or specify an appimage location with `-i <appimage>`.

## Updating

You can then use `pvim -u` to update pvim itself, your config (if it is a git
repo) and the appimage (if not using `-i`).

## pvim Specific Neovim Config
`os.getenv("PVIM")` will be set to the pvim directory when running pvim. This
can be used to enable/disable plugins depending on if running in pvim.

## Known issues

- plugins which specifically look for the xdg standard directories will not contain
their files to the pvim directory

## ToDo

- [x] Check the commands actually work
- [x] Thank the neovim matrix guys 
- [x] improve the README 
- [x] improve the update-command to update your config as well as the appimage 
- [x] Fix that one error from packer `Can't open file /path/to/manifest for writing` 
- [x] Add windows compatibility (in the lua, no pvim.bat yet) 
- [ ] Add pvim.bat 
- [x] Remove the PackerCompile workaround, or at least make it nicer 
- [x] support init.vim (Or no init) 
- [x] find other outside files that Neovim uses (e.g. undo directory) 
- [x] Add mason.nvim installation directory 
