# DEV0  A simple Development Environment for the rest of us

DEV0 provides a simple user interface for managing open source
development activity.

It organizes project materials and provides simplified developement commands across different projects
Open-source application suites might host several related repositories. Sometimes work on an application suite includes work on repositories from other organizations.
Application Suite Development Activities include formal versions, specific new features, or bug fixes.  Usually, only one or a few repositories need a different branch, while others remain on a release branch.

 Keeping all that straight can be daunting.  DEV0 provides a way to do it.



  DEV0 support such projects by 
Commands include new, build, run, git-pull, git-push, git-stash, git-branch, which direct specific actions to the currently context.

A Work on an application suite occurs on three levels

  - Suite
  - Activity (one or more)
  - Repository (one or more per activity)
  - Branch (one per repository on an activity)

DEV0 stores information about the structure of Activities on an Application suite in a set of directories and files under $DEV_USER_DATA

$DEV_USER_DATA  (usually home/.DEV0/)
---|<application-suite-name>
   ---<Activity>  
      ---<Repository>
          ---activity-repository-branch-name (a file name or file contents)

DEV0 does not use git workspaces but instead copies the entire repository and working tree for each new activity.  This makes switching between activities easy. But it makes merging more complex.

Commands:

b or build
r or run
rebuild

n or new
