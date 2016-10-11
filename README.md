# A Beginner's Guide to vim

Through your coding career, you have likely had brief encounters with vi while looking over your coworker's shoulder or tweaking a server setup script. It looks arcane, and it's hard to tell if it's just an old habit of some coders or if it will actually make you more productive.

This guide is light on actual content and is intended to provide structure for how to learn vim. In truth, the only way to learn vim is to use it. The learning curve is steep but well worth it.

## My perspective

vim is versatile, and this guide is written from the perspective an engineer who (mostly):

* uses a Mac
* `ssh` into Ubuntu virtual private servers (e.g. AWS EC2 instances)
* writes Python/Django and JavaScript/React
* builds a web application

Hopefully this guide is applicable to others as well.

## 1. Movement and editing

The basics of any text editor is being able to edit text, and vim is trickier than typing and deleting. There are plenty of cheatsheets and laundry lists of commands, so we won't add another here. The best way to learn it is to use `vimtutor`, a tutorial built into vim that you can launch from your console. Go through it first to learn the basics, then do it again in a week after using vim for real.

* [vimtutor man page](http://linuxcommand.org/man_pages/vimtutor1.html)

## 2. Split Screen

We maintain a 100 character line length in our codebase, which is less than half of the width of a 1920px screen. Typically, I keep 2 different windows open side-by-side. You can split your screen with `:vsplit` and switch back and forth with `ctrl-w ctrl-w`.

Search online for more split commands (there are a lot).

## 3. Autocomplete

`ctrl-p` is your friend. When you're typing, you can autocomplete the current word, where the options are drawn from words found in all open buffers.

## 4. Search and Search/Replace

`vimtutor` should have gotten the basics of find/replace, but here are some particular helpful techniques I have found

`#` and `*` search for the word currently under your cursor.

* [Vim Tips wiki](http://vim.wikia.com/wiki/Search_and_replace) - The "Details" section is pretty good
* [Search and Replace on Multiple Files](http://usevim.com/2012/04/06/search-and-replace-files/) - This is really great technique for doing semi-automated renaming. For doing fully-automated renaming, I recommend using `sed` or a shell script

## 5. Editing your vim configuration

vim is extremely deep because it is extremely customizable. This includes simple settings such as tab widths or case sensitivity in search, but it also includes syntax highlighting by file type and rich plugins.

My dotfiles are [available on github](https://github.com/StoicLoofah/dotfiles) to see my settings in my `.vimrc`. There are 2 semi-standard settings that have been tremendous for me personally:

* `imap jj <Esc>` - Type 'jj' to exit insert mode. This saves the stretch for the escape key or for ctrl-{
* `nnoremap ; :`, `nnoremap ; :` - You type colon far more often than semi-colon, so this swaps those

Currently, I would recommend [Vundle](https://github.com/VundleVim/Vundle.vim) as your plugin manager.

## 7. GNU screen

Technically this is outside of vim, but I find `screen` to be indispensible in my environment. screen provides virtual shells so you can rapidly switch between vim and the shell. My typical setup has 3 screens:

1. vim - I only have 1 instance of vim running at any time to avoid conflicts. I use multiple buffers and [vim-session](https://github.com/xolox/vim-session) to maintain that
2. shell - everything else I use outside of vim, including ack, git, scripts, file system management, etc.
3. server - for web dev, you usually have to run a Django/Rails/Node development server, so I just keep that running in a separate shell

* [Matt Cutts screen tutorial](https://www.mattcutts.com/blog/a-quick-tutorial-on-screen/) - the really, really short screen tutorial
* [rackaid screen tutorial](https://www.rackaid.com/blog/linux-screen-tutorial-and-how-to/) - the best screen tutorial I have found

Note that you can also create a .screenrc to customize your screens as well.

## 8. Macros

Macros allow you to record a series of commands and repeat them again. Very useful for repetitive tasks

* [Vim Tips wiki](http://vim.wikia.com/wiki/Macros)
* [rampion on how to edit multiple lines on StackOverflow](http://stackoverflow.com/a/356059) - this isn't really a macro, but it's a very common pattern that I have used

## 9. Marks

Marks record your cursor position, which you can use as a "bookmark" or in combination with other commands. I usually use uppercase marks because I'm bouncing between so many files

* [Vim Tips wiki](http://vim.wikia.com/wiki/Using_marks)

## 10. Registers

Registers are basically a multi-clipboard. I like using registers when I am replacing repetitive code since the unnamed register keeps getting overwritten when I delete lines of code.

* [usevim](http://usevim.com/2012/04/13/registers/)

## 11. References

* [Jim Dennis on grokking vi](http://stackoverflow.com/a/1220118) - a long but also deep StackOverflow answer on how vim works
* [Vim Tips wiki](http://vim.wikia.com/wiki/Vim_Tips_Wiki) - it's not very well-organized, but you will stumble across this site often while googling for vim tips
* [Vim Awesome](http://vimawesome.com/) - index of vim plugins
* [List of Django dev tools](http://blog.zanbato.com/2014/10/07/useful-tools-for-django-development/) - for life outside of vim, here's a full stack of tools you can use for Django development

## 12. So much more!

Although this guide is a quick read, learning to use vim can take a long time. While you are coding, be aware of the tasks at hand and keep that meta-awareness about what vim tricks you might use to be more efficient. Over time, more of it will become automatic, and everything will feel quick and intuitive.

Beyond this guide is a world of customizations and additional shortcuts to continue to learn.
