# nvim

A [Notational Velocity][nv] inspired mode for [vim][]. 


## Requirements
This should work on any recent vim compiled with `+python`. You will also need the [xapian][] library and python bindings. Note that xapian does not currently work with python3.

## Installation
Easiest way is to use [pathogen][]:

````
cd ~/.vim/bundle
git clone git://github.com/cwoac/nvim.git
````

Or if you manage things yourself, copy `nvim.vim` into your ~/.vim/plugins directory.

### Script

NVim is not intended to be used in every vim session you open; to this end it will not be activated until you `:call NVIM_init()`

There is a supplied script `nvim` which will open vim and call this to drop you directly into nvim mode; simply copy it to somewhere on your path

## Usage

I've made a quick screencast [here](http://showterm.io/3668688fe06b53482da16) outlining basic usage.

run `nvim` from within that directory. You will be presented with two windows - on the right is the main pane where the note is displayed; on the left the list of search results.
The first line of the search box is the current search term.

Use `[[` to trigger vim's auto-complete with the list of available titles.

nvim binds several keys, all combos are started with the user's defined `<leader>` key. If you haven't changed this, then it is `\` by default.

* `\<F5>`  Invoke NVIM on the current directory. This is the only key bound until NVIM has been invoked once. Hitting it a second time will do nothing.
* `\<cr>`  This will follow a '[[...]]' link from within a note.
* `\l` Move the cursor to the search area ready for changes.
* `\i` As `\l`, but clears the current search term first (equivalent to `<esc>` on NV as remapping escape in vim is... unwise)
* `\d` Delete a note. **warning** This will delete the note pointed to by the search bar. Under normal usage this should be correct. 
 It does not currently ask confirmation.
* `\r` Rename a note. This will *not* update any links in other notes.


Note that if you try an load a note that does not exist, the system will create a new one.

The full range of vim commands are available to you, but there are a couple of things to bear in mind:

* Autosave is turned on
* You can create new windows via splits or whatever as you wish - when a note is loaded from the search results it will be loaded into the most recently used window.
* If you close the results window (or all windows apart from the results window) you will need to close and reopen vim.
* If you delete a note or alter the contents of notes outside of nvim, then you can refresh the database as under _importing_ below.

### Configuration
configuration is handled at the top of `nvim.vim`. The main one is the extension for notes. By default, nvim uses `.md` and will ignore files with any other extension.

### Importing
If you have a bunch of notes already, then execute the following command to import them `:python nvimdb.rebuild_database()`. 

## TODO
Quite a few things, although the code is quite usable as-is.

* Allow hiding/reshowing the search results
* Some proper documentation (screencasts!)

 [nv]: http://www.notational.net
 [vim]: http://www.vim.org
 [xapian]: http://xapian.org
 [pathogen]: https://github.com/tpope/vim-pathogen
