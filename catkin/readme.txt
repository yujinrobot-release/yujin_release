Each folder is a different set of stacks we're catkinizing.

See https://github.com/yujinrobot-release/yujin_release/wiki/Release---Groovy-Wet

In short, usual workflow in one of those folders:

> make clone
> do prerelease tests
> bump version numbers in the sources
> create new tags in the source folders 
> make bloom
> make push

You might need to edit the makefile and redefine the array for a single stack. That
can be easer debugging than trying to bloom all stacks at once.
