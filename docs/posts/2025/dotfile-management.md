---
date:
  created: 2025-09-09
authors:
  - michaeltinsley
categories:
  - Projects
  - Tools
---

# Taming My Dotfiles with GNU Stow

For the longest time, my dotfiles were an afterthought. I, unlike _most_ developers, was pretty happy with the default configurations of my tools. Setting up a new machine was a tedious manual process (albeit often quite therapeutic) of reinstalling everything and tweaking a few settings from memory. It worked, but it was far from efficient.

I'd heard of dotfile management and even attempted to use Chezmoi a few times, but I found the workflow a bit too complex for my taste. I needed something simpler, more intuitive. That's when I discovered GNU Stow, and found a happy medium.

## What are Dotfiles Anyway?

For those unfamiliar, "dotfiles" are configuration files for various programs on your system. They're named this way because their filenames start with a dot (e.g., `.bashrc`, `.vimrc`, `.gitconfig`), which typically hides them from view in file explorers. These files are the secret sauce that makes your development environment yours.

## Why Bother Managing Them?

The "why" is pretty simple - typically dotfiles are tailored to your preferences, and this can take a while to slowly perfect. Once you have your applications configured to your liking, you want to be able to save these settings and easily replicate that setup on new machines. This also enables you to version control your dotfiles, making it easy to share and collaborate with others. Additionally, it allows you to easily revert to previous configurations if needed.

## Getting Started with My Dotfiles (and GNU Stow)

Now, whenever I provision a new machine, I simply install Stow, clone the repo, and create the symbolic links.

```shell
# Install Stow via Homebrew
brew install stow

# Navigate to the home directory
cd ~/

# Clone the dotfiles repository
gh repo clone michaeltinsley/dotfiles

# Stow the desired application's config
stow ghostty
```
This command will create a symbolic link from the `ghostty` directory in the dotfiles repo to the corresponding location in your home directory.

## Why Stow Over Chezmoi?

As I mentioned earlier, I found Chezmoi's workflow to be a bit more than I needed. Stow's simplicity is its greatest strength. It does one thing and does it well: it manages symbolic links. This straightforward approach resonates with me and makes managing my dotfiles a painless process.

That said, there are features of Chezmoi that I wish Stow had. These are primarily around secrets and templating. Chezmoi integrates with several different secrets providers, allowing the injection of secrets into templated configurations. It also makes it possible to template out different configurations depending on the machine—for example, I can set my personal email for Git on my personal machine, and my work email for Git on my work machine.

I still like the idea of migrating to Chezmoi for these features, so maybe one day I will put the time into learning it and migrating my dotfiles. But at the same time, I worry that it'll be a time sink for me and I'll be forever trying to perfect things.

## Conclusion

Investing a little time in setting up a dotfiles management system has paid off. My development environment is now consistent, portable, and backed up. If you've been on the fence about using a dotfiles management system, I highly recommend giving Stow a try.
