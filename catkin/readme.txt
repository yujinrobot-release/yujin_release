Each folder is a different set of stacks we're catkinizing.

See https://github.com/yujinrobot-release/yujin_release/wiki/Release---Groovy-Wet

If it's the first time you're building, you need to 

* Make the release repo with name "myreponame-release"
* Create a folder here and copy one of the other Makefile's across, edit the repos
* make clone
* make config
* make push

Otherwise, the usual workflow in one of those folders:

> make clone
> do prerelease tests
> bump version numbers in the sources
 > cd source_repo
 > catkin_package_version --bump patch
 > git commit -a -m "x.y.z"
 > git push
> create new tags in the source folders 
 > cd source_repo
 > git tag x.y.z -m "first catkinization"
 > git push --tags
> make bloom
> make push

You might need to edit the makefile and redefine the array for a single stack. That
can be easer debugging than trying to bloom all stacks at once.

Finally, once all your stacks are good to go, edit the version number in 
https://github.com/ros/rosdistro/blob/master/releases/groovy.yaml to match the latest
version number in your source/release repos.
