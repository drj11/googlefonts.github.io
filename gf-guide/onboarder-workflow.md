<link href="style.css" rel="stylesheet">

<a href="./index"><button class="button button-i">&larr; GF Guide Index</button></a>

# Onboarder workflow guide
{:.no_toc}

<div class="callout">

🐝 Google Fonts has become too big to be maintained as a simple community repository. The platform is now an API distributing and serving more than a thousand fonts families, and GF has started to see itself as a proper open-source foundry.

This means several things:

<ol>
    <li> While in the past spontaneous contributions were still possible, today the specifics of the requirements and the security in place have made it complicated for a random user to make such a contribution. As an example, the continuous integration (CI) can only get triggered if a pull request (PR) has been made by someone with permission to the repo. If a user makes a PR, it will definitely draw some attention, but the PR often needs to be re-done by a team member. So while contribution to the repo is not in theory exclusive to the “onboarders” (paid contractors), it tends to be in practice.</li>
    <li> GF has commissioned hundreds of fonts from professional type designers. To onboard these projects (from the moment the font family is “ready”), GF needs a toolchain that automates most of the repetitive tasks such as packaging the fonts (<mark class=grey>gftools packager</mark>) and generating QA proofs (<mark class=grey>gftools qa</mark>).</li>
    <li>The workflow must leave no place to doubt about the status of the project. Indeed, once merged into the <mark class=grey>google/fonts</mark> repo, the font actually still travels through different servers before appearing on the API. It has often happened that fonts have never got into production — because they have been forgotten in the sandbox server or somewhere else.</li>
</ol>

This workflow described below was designed so that GF do not lose products during the validation process, to facilitate the validation process, and to keep people updated about the status of different projects. It requires active maintenance and regular updates from team members.
<br><br>
It seemed also important to keep the whole status of the repository in one place, mostly to avoid copy-pasting PR links all the time. GF, therefore, chose a complete Github-based workflow, making extensive use of the <a href="https://github.com/google/fonts/issues">issue tracker</a>, the <a href="https://github.com/google/fonts/milestones">milestones</a> feature, the <a href="https://github.com/google/fonts/projects">project boards</a>, and the <a href="https://github.com/google/fonts/actions">continuous integration system</a>.
<br><br>
This guide will help team members to understand the validation process of a font family and the actions required from them to help that process.
<br><br>
→ <a href="https://google.github.io/fonts/">google.github.io/fonts</a> is a page updated weekly that reports on activity in the <a href="https://github.com/google/fonts">google/fonts</a> repo.

</div>

<div class="context-reading">
    Background reading:<br>
    <mark class="purple">nerd&nbsp;</mark> <a href="./googlefonts">google/fonts repository explained</a>
    <br>
    <mark class="purple">nerd&nbsp;</mark> <a href="./making-pr">Making a PR to Google Fonts</a>
</div>

## Table of contents
{:.no_toc}
* TOC goes here
{:toc}

## Issue tracker

[Issues](https://github.com/google/fonts/issues) from the `google/fonts` repository are used to define the Google Fonts production pipeline for team members, and for users to report bugs or suggest new submission ideas.

Since `google/fonts` only hosts binaries, and since we want these files to be in sync with the ones in the upstream repositories, onboarders manage the sources and builds from the upstream repo. This link between what happens upstream and what is reported downstream is made through the issues.

Example: <https://github.com/google/fonts/issues/3730>

<figure>
<img src="images/onboarder-workflow/Capture_decran_2022-02-23_a_13.47.57.png" style="width:2568px" alt="Screenshot of an issue from google/fonts issue tracker." />
<figcaption aria-hidden="true">Screenshot of an issue from google/fonts issue tracker.</figcaption>
</figure>

The issues should follow these rules:

-   **One issue per font family.**

    Onboarders can also use the issues as a progress tracker of their assigned projects by adding a checklist in the first comment and regular notes.

-   **They have labels**.

    At least a *primary category label* (start with `I`). Further information about labels below.
    
    E.g <mark class=grey>I Font bug</mark>.

-   **There should be a new issue for any new project commissioned** 

    And that even before delivery from the designer. These should have the label <mark class="green">commissioned</mark> and **should be into a milestone**. A non-commisioned project’s issue is assigned to a milestone if we plan to take care of it.

-   **Issues in milestones should be assigned to an onboarder.**

    Sometimes they are not assigned for a while, but any issue planned for this quarter or the next should have an onboarder assigned and also added in their project board. Otherwise no one will take care of it.

-   **The original authors of the font should be tagged in the related issue.**

    The issue become then the place for the designer update us about his progress and notify onboarders that the font is ready for review. If they have a problem, they can also report it there and link to the specific issue; this way we have a good track of the different events that stop us from onboarding a font.

-   **An issue should be linked to the PR that fixes it.**

    This allows automatic closing of the issue when the linked PR is merged.

-   **An issue must contain a link to a font’s upstream repo**

    Sometimes, multiple sources of a font can exist on GitHub, or a source may be difficult to find. To make life easy for onboarders, a link to the source repo must be included.


## Milestones

[Milestones](https://github.com/google/fonts/milestones) are used to have an overview of the upcoming year, and to divide the workload into reasonable charges.

-   **They are divided into quarters.**

-   **They should contain every issue about commissioned projects**, 

    Same for non-commissioned projects (<mark class="green">accepted</mark>) that we intend to onboard that quarter.

-   [**Important projects to be commissioned and milestoned**](https://github.com/google/fonts/milestone/23) **is the milestones for issues posted by users that we consider worth taking care of.** 

    They should be placed into a Quarter milestone when commissioned or assigned.

-   **We assess the milestones at the end of each quarter**
    
    We close them when the due date is passed. The issues that were not completed before the end of the milestones get moved to the next milestone.

-   **Issues in milestones should be assigned to an onboarder** 

    They should be placed into their respective project board.

-   **Milestones are for issues only; there are no PRs in milestones.**


<figure>
<img src="images/onboarder-workflow/Capture_decran_2022-03-18_a_12.02.19.png" style="width:2450px" alt="Screenshot of a quarter Milestone."/>
</figure>

## Pull Requests

To make a change to the `google/fonts` repo, onboarders submit a [Pull Request](https://github.com/google/fonts/pulls) which is then reviewed by a team member. According to the result of this review, the PR is merged or not.

Example: <https://github.com/google/fonts/pull/4320>

<figure>
<img src="images/onboarder-workflow/Capture_decran_2022-02-23_a_14.15.22.png" style="width:2562px" alt="Screenshot of a Pull Request from google/fonts PR tab." />
</figure>

PRs should follow these rules:

-   **Each should be linked to the issue it fixes.**

-   **They should be added to Traffic Jam** if the changes they bring should be carried out to the API.

-   **They should have labels.** 

    At least 2: a *status label* (start with `-` ) and a *category label* (start with `I`). More info about the labels in the section below. 
    
    E.g <mark class="yellow">- Ready for review</mark> <mark class="grey">I New font</mark>.

-   **The issue is closed when the linked PR is merged.** 

    If the PR has been properly linked to an issue, then this action is automated. This can cause confusion in the sense that the users will think that when the issue is closed, then the issue is fixed. But the fix carried out by the PR only gets mirrored on the API after validation in the sandbox server and push to production (cf Pull Request Review below). Therefore a few weeks can pass in between. This system is not ideal, but it saves us from manually closing multiple issues when the changes are live.

-   **If the PR gets “blocked” after merging, the issue should be manually reopened** and fixed with another PR.

-   **A reviewer should be assigned if the PR needs to be reviewed by someone in particular.**

    Otherwise no need to do it, and the current reviewer will do it if your PR is <mark class="yellow">Ready for review</mark>.

-   **If the PR was made by a user or non-contributor to the repo, it could be assigned to a team member to take care of it.**

    Most of the time, a team member will have to re-do it because of credentials activating the CI, and general workflow and requirements that are often not respected by non-usual contributors.

## Project boards

PRs and issues are monitored in separate Github project boards.

-   **Each onboarder contracted by GF has a personal project board**

    They manage their own workload / issue list.

-   **There are only issues in an onboarder’s board.**

    Since PR and issues are linked, it is then easy for an onboarder to check the status of his PR. So no need to add PRs in one’s personal project board.

    <figure>
    <img src="images/onboarder-workflow/Capture_decran_2022-02-23_a_14.39.16.png" style="width:2228px" alt="Screeshot of an onboarder’s project board" />
    </figure>

-   **PRs are added to the Traffic Jam project.**

    There are only PRs in this project board, as it is meant to monitor the status of the PR’s content from submission to publication, knowing that its content is supposed to be pushed to 3 different servers: the *developer sandbox*, the *sandbox*, and finally the *production* Google Font API.

-   **Always add labels to items you want to track.**

    The combination of labels and project boards allow us to track progress, write the push lists, and build stats using different scripts. Therefore **the labels and Traffic Jam board should not change** name without also changing the [gftools gen-push-lists](https://github.com/googlefonts/gftools/blob/main/bin/gftools-gen-push-lists.py) script.

    <figure>
    <img src="images/onboarder-workflow/Capture_decran_2022-02-23_a_14.40.21.png" style="width:2968px" alt="Screenshot of the Traffic Jam project board that monitors PRs" />
    </figure>

## Labels

[The labels](https://github.com/google/fonts/labels) are extremely important in this workflow. They help communication between users, reviewers and onboarders. Scripts and issue templates are also linked to specific label names to generate reports and statistics, and so names should not change without updating the scripts.

### Category

**`I` Primary: Issue and PR** [grey]
    
<mark class ="grey">New font</mark> 
<mark class ="grey">Font upgrade</mark> 
<mark class ="grey">Designer profile</mark> 
<mark class ="grey">Description/Metadata/OFL</mark> 
<mark class ="grey">Font bug</mark> 
<mark class ="grey">Request</mark> 
<mark class ="grey">Axis Registry</mark> 
<mark class ="grey">API/Website/Platform</mark> 
<mark class ="grey">Tools/workflow/repo</mark> 
<mark class ="grey">Knowledge</mark>

**`II` Secondary:**
    
- prioritisation for new fonts [light green]: 
<mark class="green">Commissioned</mark> 
<mark class="green">Accepted</mark> 
<mark class="green">Submission</mark> 

-   primary script [dark green]: 
<mark class="darkgreen">CJK</mark> 
<mark class="darkgreen">Indic</mark> 
<mark class="darkgreen">Arabic</mark> 
<mark class="darkgreen">Icon</mark> 
*→ you can create new label if the script is not there*

**`III` Additional: to specify the type of upgrade** [light orange]
    
<mark class="orange">Expand glyphset</mark> 
<mark class="orange">Expand styles</mark> 
<mark class="orange">Improve rendering</mark> 
<mark class="orange">Small Fix</mark> 
<mark class="orange">VF Replacement</mark>

### Status

Status labels are having meaningful colours:

- <mark class="yellow">**YELLOW** | Process can continue to next step</mark>
- <mark class="orange">**ORANGE** | Process in progress</mark>
- <mark class="blue">**BLUE** | Process pending until more information</mark>
- <mark class="red">**RED** | Process is on hold, fixes required before proceeding</mark>
- <mark class="black">**BLACK** | Process is blocked and should begin again</mark>

Labels also have meaningful prefixes:

-   `-` **Submissions:** (Issues and PRs)

    <mark class="yellow">Ready for review</mark>, 
    <mark class="orange">In progress</mark>, 
    <mark class="orange">Upstream is working on it</mark>.

-   `—-` **Result of review:** (Issues and PRs)
    
    -   Usually for font bugs

        <mark class="red">Bad rendering</mark> 
        <mark class="red">Glyphset Issues</mark> 
        <mark class="red">Needs design work</mark> 
        <mark class="red">Requires axis registration</mark>

    -   Usually after reviewing repo/PR:

        <mark class="red">Needs Meta/Desc/License changes</mark> 
        <mark class="red">Needs upstream resolution</mark> 
        <mark class="red">Regression</mark> 
        <mark class="red">Missing sources</mark> 
        <mark class="red">Has RFN</mark>

    -   Needs more info:

        <mark class="blue">Needs confirmation</mark> 
        <mark class="blue">Needs Dave’s opinion</mark>

-   —-- **Servers status:** (Only *merged* PRs)
    
    -   Lists:

        <mark class="blue">to sandbox</mark> 
        <mark class="orange">to production</mark>

    -   Servers:

        <mark class="yellow">In sandbox</mark> 
        <mark class="green">Live</mark>

    -   Problem after merging:

        <mark class="black">Blocked</mark> 
        <mark class="red">API Tofu</mark>

## The servers validation process

1.  The google/fonts repo is linked to a dev-sandbox. A few hours after a change to the repo (once a PR gets merged for example), this change is reflected on that server.

    → These servers act like steps in a pipeline: the change must be uploaded into the `dev-sandbox` before it can be be pushed in the `sandbox`. Similarly, a change can’t be pushed to `production` (live server) if it hasn’t been pushed to `sandbox` first.

2.  Once a week, the lists of changes to push to `sandbox` and to `production` are generated with the script [gftools gen-push-lists](https://github.com/googlefonts/gftools/blob/main/bin/gftools-gen-push-lists.py): it updates the [to_sandbox.txt](https://github.com/google/fonts/blob/main/to_sandbox.txt) and [to_production.txt](https://github.com/google/fonts/blob/main/to_production.txt) files that instruct the engineers team which changes they should push to the different servers.

    → When the changes are added to these lists, we can move the PRs into the corresponding columns (`In Sandbox list`, `In Production list`).

    → The script uses the labels to categorise correctly the changes in the list files.

3.  When the changes are pushed, they get reviewed again. If validated in `sandbox`, they can be pushed to `production`.

    → The status label can be changed to <mark class="brown">to production</mark>.

    → The push to sandbox and production are staggered biweekly, so each week should happen at least on push to one of the server

    → When the changes are pushed to production, the label can be changed to <mark class="green">Live</mark>

## Example of workflow

1.  An issue is opened by a user to request the addition of a new font family: “My New Font”. The font is ready to be onboarded upstream, and the user has complied with all the requirements.
    -  **Title:** `Add My New Font` 
    -  **labels:** <mark class="grey">New font</mark>, <mark class="green">Submission</mark>

2.  A team member inspects the font files and sees good potential. They add the label <mark class="blue">Need's Dave opinion</mark> to check with Dave Crossland (Program manager) if the font is worth being onboarded.

3.  Dave is thrilled, he loves the font and wants it in the library. He removes the label <mark class="blue">Need's Dave opinion</mark> and adds the label <mark class="green">Accepted</mark>. He adds the issue to a convenient milestone, and during a quarterly meeting where milestones are assessed, he will assign the issue to an onboarder and it gets added to their project board.

4.  The onboarder starts to work on the project upstream. They add the label <mark class="orange">In progress</mark>. While doing QA on the font, they notice some design issues that need to be addressed by the designer. They add the label <mark class="red">Needs upstream resolution</mark> to the issue to notify that this project is on hold until the issues are resolved by the designer.

5.  The designer makes the requested changes and notifies the onboarder by commenting on the issue. *Et cetera*.

6.  When the font is built and the QA is good, the onboarder ships the font to `google/fonts` by making a Pull Request.
    -  They add the PR into the` Traffic Jam` project.
    -  They add at least 2 labels to the PR: a *category* (<mark class="grey">new</mark>, <mark class="grey">upgrade</mark>, <mark class="grey">designer</mark>…) and a *status* (<mark class="orange">in progress</mark>, <mark class="yellow">ready for review</mark>…).

7.  Then, the PR gets reviewed by a team member. The status label is updated according to the result of that review. This time, the reviewer spotted a regression in the spacing, and needs to know if it is a mistake or an improvement. They post an image of the issue and add the label <mark class="blue">Needs confirmation</mark>.

8.  The onboarder checks with the designer, who decides that the regression is a mistake. They change the PR label to <mark class="red">Needs upstream resolution</mark>.

9.  Once the mistake is fixed, the onboarder updates the PR with the newly build fonts, and changes the status label to <mark class="yellow">Ready for review</mark>. Now we go back to the same process as before, but this time the reviewer approves the PR and merge it.

10. When the PR gets merged, it goes automatically in the the column `Just merged / in transit` of the `Traffic Jam` project. A few hours later, the new font will appear in the `dev-sandbox`, and if it looks good, the label `to sandbox` can be added to signify that this font can be pushed to sandbox.

11. In parallel of that process the onboarder should have prepared a tweet to officially communicate the font’s arrival on Google Fonts.

The onboarder’s job is done. The font still needs to get through the servers validation process described [above](onboarder-workflow.md), and if everything goes smoothly, the font should be live on [Google Fonts](https://fonts.google.com) after few weeks.
