# Preparation

The following uses the hypothetical repo _foo_.

* Create a [new repository](https://github.com/organizations/yujinrobot-release/repositories/new) called _foo-release_.
 * Initialise it with a README.
* Clone the release repository locally and configure it with bloom for indigo.

```
> git clone https://github.com/yujinrobot-release/foo-release
> cd foo
> bloom-release --rosdistro indigo --track indigo foo --edit
```

Options to configure:

* First provide a link to the release repo to get it started: `https://github.com/yujinrobot-release/foo-release.git`
* _Repository Name_: foo
* _Upstream Repository URI_: url to your code repo, e.g. `https://github.com/stonier/foo.git`
* _Version_: :{auto}
* _Release Tag_: :{version}
* _Upstream Devel Branch_: usually 'indigo'
* _ROS Distro_ : indigo
* _Patches Directory_ : None
* _Release Repository Push URL_: None (it will use your first supplied release URI by default)
* _Releasing Complete, push?_ : yes
* _Add Documentation?_ : yes if you have sphinx/doxygen organised, no otherwise.
* _Add Source Information?_ : yes, this lets you pre-release test off the latest commits
* _Add Maintenance Status?_ : yes, either 'maintained' or 'developed'.


