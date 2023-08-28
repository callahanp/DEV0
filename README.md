# DEV0  A simple Development Environment for the rest of us

DEV0 provides a simple user interface for managing open source
development activity.

It organizes project materials and provides simplified developement commands across different projects
Open-source application suites might host several related repositories. Sometimes work on an application suite includes work on repositories from other organizations.
Application Suite Development Activities include formal versions, specific new features, or bug fixes.  Usually, only one or a few repositories need a different branch, while others remain on a release branch.

 Keeping all that straight can be daunting.  DEV0 provides a way to do it.



DEV0 supports such projects with commands including new, build, run, git-pull, git-push, git-stash, git-branch, which direct specific actions to the current context.

Work on an application suite can proceed in any of three directory levels

  - Suite
  - Activity (one or more)
  - Repository (one or more per activity)


DEV0 does not use git workspaces but instead copies the entire repository and working tree for each new activity. This approach makes switching between activities easy. But it makes merging more complex if there are many active activities.

Commands:

b or build
r or run
rebuild

n or new


## Suites

Ensure there is a $DEV0_TREES/$suite directory with a git repo
unconnected or connected via git-remote

### Suites Actions

Either:
a: Clone an origin or upstream url into $DEV0_TREES/$suite 
  or 
b: Create $DEV0_TREES/$suite directory
and Initialize a .git in $DEV0_TREES/$suite directory
Choice of a. or b. depends on 
supplying or not supplying 
 a $suite_origin_url 
 or $suite_upstream_url

### Suites - Background Info

A suite may or may not have a .git associated with only
the suite and any contained Activity directories.  This 
repository is limited to exclude any suite component repositories.

If $suite_origin_url is provided, use it for the clone 
and then if there is a $suite_upstream_url, add it the .git
if neither is supplied, use option b.

Suite folders are identified by the presence of a file named
<suite-name>.suite.  They may also contain a single default 
activity indictated by the presence of a file named 
<suite-name>.activity
a script for receating the suite can be placed in 
$DEV0_TREES/$suite after it is created.

## Activities

Ensure that there is a $DEV0_TREES/$suite/$activity directory
created if the user specifies one otherwise use $DEV0_TREES/$suite.

Ensure the creation of a .git repository if an Activity git repository is needed.

### Activities - Actions:

Figure out if the .git should be in  $DEV0_TREES/$suite/ or
$DEV0_TREES/$suite/$activity

if an origin or upstream url is given
and there is no clone a git origin or git upstream repository in place
clone the origin or upstream repo

Ensure that if an origin or upstream url is given for the activity 
and the given remotes are in place

Ensure that if an activity git is requested without upstream or origin urls, 
it is in place.

### Activities - Background

An activity may or may not have a .git associated with only
the activity. This repository is limited to exclude any suite 
component repositories.

Activity folders are used to hold copies of the suite's .git repositories. 
Separate activity directories are needed to support work on different
versions or new branches. 

The activity name might reflect which of these is being worked on
It usually does, but branch and tag names are specific to the individual 
repositories, activities cover one or more repositories and name a folder
in dev0. Allowable characters in Activites are [a-zA-Z0-9_-.].An exact
match to a branch in one of an activities repositories is not required.

The following are acceptable as Activity names:

some-random-allowable-name
release_3.0 (happens to be a tag in the main repository), 
myFeatureBranch (a new branch in my local .git)

Activities are not required if there is only one activity. This would be the case 
for a suite you just want to build and use.If there is more than one activity, 
its recommended that you use an activity for all of them.

Activity directories are identified by the presence of an empty file named
<activity-name>.activity.If there is only one activity and an activity folder 
is not desired, <activity-name>.activity is placed in $suite.

a script for receating or validating the activity can be placed in 
$DEV0_TREES/$suite after it is created.

# Repositories:

Ensure that there is a $DEV0_TREES/$suite/$activity/$repository
or $DEV0_TREES/$suite/$repository directory and that it has a
.git, either initialized or cloned from an origin or upstream url

# Repositories - Actions

# Repositories - Background

A repository is needed in an activity or suite for each component 
that will be modified, or needs to be custom built to work on the suite as a whole.


Repostories are named based on the name in the origin_url, or if given
a recognizable but simpler local name provided in the Repository parameter
To use the name in the origin_url specify "Repository" "". Otherwise, fill
  in the empty string with the name you want to use.
