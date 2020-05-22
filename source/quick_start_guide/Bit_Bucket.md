## What Is Bit Bucket?

Bitbucket is a web-based hosting service that is owned by Atlassian,
used for source code and development projects that use either Mercurial
or Git revision control systems.

## Getting Started

### Create an Account

1.  Navigate to: <https://www.bitbucket.org>
2.  Create an account with your University email.

\*\# Afterwards, your account should automatically be converted to an
unlimited academic plan.

### Create a Team

1.  Log in and click the "+" sign on the left pane.

\*\# You should be able to even login with Google - no password
required\!

1.  Under the "Create A New" submenu, click "Team".

\*\# Team names should follow the naming scheme: "DEAC_researchGrp"

\*\# This is where research group member emails are added

1.  Once a team is created, a link to create a new Repository will
    appear

### Create a Repository

1.  Click the "+" sign on the left pane.
2.  Click "Repository" under "CREATE A NEW"
3.  In the new menu, select a pre-existing "Project name" or create a
    new one.
4.  Provide a relevant repository name.
5.  Ensure "This is a private repository" remains checked if to be seen
    by your group only.
6.  Leave "Git" as the Version Control System

\*\# Under advanced, add a description and specify code type if desired.

1.  Once the repository is created, lists below "Get started with
    command line" will provide steps to use your new repo\!

### Using a New Repository

1.  After creating your repo, an "I'm starting from scratch" link will
    provide exact steps to use from
    headnodes.

<!-- end list -->

    git clone https://loginName@bitbucket.org/DEAC-researchGrp/repositoryName.git
    cd repositoryName
    echo "# My project's README" >> README.md
    git add README.md
    git commit -m "Initial commit"
    git push -u origin master

1.  Those steps will copy your repository locally, create a new file,
    and push it remotely.

## Troubleshooting

### Academic Plan Enrollment

  - If not automatically enrolled into an academic plan, one of two ways
    can be used

:\* Complete \[this
form|<https://www.atlassian.com/software/views/bitbucket-academic-license.jsp>\].

  - OR

:\* Change your plan manually

::\* Log in to your account, click the user icon and "View Profile"

::\* Under Plans and Billing, click "Plan Details"

::\* If it does not state "You're on the Academic (tiered) plan.", click
"Change plan"

::\* Scroll down and click "apply to have your institution added."

  - All users on your team should have the academic plan once fixed

## See Also

  - [Quick Start Guide:GitHub](Quick_Start_Guide:GitHub "wikilink")
  - [Quick Start Guide:Git
    Migration](Quick_Start_Guide:Git_Migration "wikilink")

## References

<references/>

[Category:Quick Start](Category:Quick_Start "wikilink")
[Category:Revision Control](Category:Revision_Control "wikilink")
