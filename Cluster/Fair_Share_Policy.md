## Basic Principles

The general goals of this fair share policy are:

1.  Courses or other educational uses of the cluster will always have
    the highest priority. Course instructors may even request exclusive,
    dedicated use of a limited portion of the cluster for student use in
    class or laboratory sections.
2.  Fair share calculations for a particular research group will be
    derived from monetary funds from grants or internal sources that are
    then provided to a particular individual and contributed to the WFU
    DEAC Facility.
3.  Research groups or individual users, who have received an account in
    accordance to the [Account Management
    Policy](Cluster:Account_Management_Policy "wikilink") but have not
    yet contributed to the cluster, will gain low priority access at a
    level defined by the **General Group Fair Share Target**.
4.  Contributions to the cluster will directly affect a research group's
    fair share calculation during the grace period.
5.  Contributions to the cluster will have reduced affect on a research
    group's fair share calculation after the grace period.
6.  The grace period and decay rate for a given contribution in a given
    year are fixed for those contributions and will not change during
    the life of that contribution. Retroactive changes to those values
    will not be allowed.

## Brief Summary of Fair Share Calculation and Usage

All **contributed funds** have an **apparent value**.

  - This apparent value will be 100% of the funds for the duration of
    the **Fund Grace Period**.
  - After the **Fund Grace Period**, the apparent value will be reduced
    each year by the **Fund Decay Rate**.

The **Individual Fair Share Target** for a principal investigator (or
group of PIs) is the percentage of the **Total Cluster Contributions**
that the PI's (or group of PIs) **Individual Contribution** occupies. A
portion of the **Individual Fair Share Target** of the default
(non-contributor) user group (also referred to as the **General Group
Fair Share Target**) is then added to each PI/co-PI **Individual Fair
Share Target**.

  - **Individual Contribution** is the sum of the **apparent value**s
    for all contributions made by the PI (or group of PIs).
  - **Individual Contribution** for the default (non-contributor) user
    group is the sum of the **apparent value**s for all contributions
    made to the cluster as a whole (i.e. University administration
    funding, grants for the cluster as a whole, etc.)
  - **Total Cluster Contributions** is the sum of all **Individual
    Contribution**s by both PI/co-PI and to the default user group.

When there are insufficient resources to begin job execution, enqueued
jobs will be prioritized based on a PI/co-PIs cluster usage history and
their **Individual Fair Share Target**. The priority scheme will work
toward ensuring that, under insufficient computational resource
conditions, PI/co-PIs will receive a percentage of cluster resources
specified by their **Individual Fair Share Target**. When jobs are
enqueued, prioritization for execution will be determined by the
scheduler, using **Individual Fair Share Target** and job resource
requirements to determine running order as computational resources
become available.

Detailed formulas for the behavior defined in this section can be found
below in [Apparent Value
Calculation](Cluster:Fair_Share_Policy#Apparent_Value_Calculation "wikilink")
and [Fair Share
Calculation](Cluster:Fair_Share_Policy#Fair_Share_Calculation "wikilink").

**Note:** All bold face terms in this section are defined below in the
[Common Terms](Cluster:Fair_Share_Policy#Common_Terms "wikilink")
section.

## Rates and Constants

<table style="width:95%;">
<colgroup>
<col style="width: 23%" />
<col style="width: 71%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;"><p>Rate/Constant</p></th>
<th style="text-align: left;"><p>Value for FY</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Fund Grace Period</p></td>
<td style="text-align: left;"><p>4 years</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Fund Decay Rate</p></td>
<td style="text-align: left;"><p>40% of original amount each year outside of grace period</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Educational/Courses Using the Cluster [1]</p></td>
<td style="text-align: left;"><p>100% of Actual Cluster Usage by Course, up to a maximum of 4 node-months per student</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p><strong>Funded</strong> Grant Proposals<br />
Research Group Specific [2]</p></td>
<td style="text-align: left;"><p>100% of awarded cluster funding</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Facilities Funding Coordinator(s) [2],[3]</p></td>
<td style="text-align: left;"><p>50% of funding secured for the Cluster Facility, split between participating coordinators</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p><strong>Funded</strong> Grant Proposals<br />
Cluster Facility [2]</p></td>
<td style="text-align: left;"><p>50% of awarded cluster facility funding is applied to the general user category</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
</tbody>
</table>



  - Footnotes :
    \[1\] Credit toward fair share will be applied at the end of the
    semester during which the course was held.
    \[2\] Credit toward fair share will be applied no sooner than the
    transfer of funds to the WFU DEAC cluster facility and no later than
    the end of the same semester. The exact date of credit within that
    window is at the discretion of the principal investigator(s).
    \[3\] Facilities Funding Coordinators refers to researchers who
    coordinate facility level grant funding with external funding
    agencies or secure institutional funding through efforts on behalf
    of the cluster facility.

## Sharing of Fair Share Credits

  -
    Fair share credits shall be split among the participating principal
    investigators (PPIs) as specified by unanimous consent of those
    PPIs. By default, unless instructed otherwise by those PPIs, the
    fair share credits shall be split equally among all PPIs. If there
    is a desire for non-default sharing but unanimous consent is not
    possible, the fair share allocation will be subject to the [terms of
    arbitration](Cluster:Fair_Share_Policy#Arbitration_Responsibility "wikilink")
    of this policy.

## General Group Fair Share Contributions

  -
    Wake Forest University institutional funds from any non-Sponsored
    Program source provided for the cluster facility as a whole shall be
    attributed to the **General Group Fair Share Target** provided they
    fund the following expense categories:
    :\# Software Licensing Fees for General Use software (compiler
    licenses, for example)
    :\# Infrastructure Hardware Expenses (network switches, for example)
    :\# Hardware Site Operational Expenses (co-location costs, for
    example)

## Arbitration Responsibility

  -
    The WFU DEAC Facility Representative Committee shall be the sole
    arbitrator for disputes in the apportionment of shared fair share
    allocations outlined in this policy.

## Explicit Intent of Policy

  -
    Under no circumstances shall the edits or rough drafts or history of
    this policy that results from the technology used to create and
    display this policy be used to imply any meaning other than that
    clearly stated in the written words of the latest version of the
    policy and approved by the WFU DEAC facility Representative
    Committee and
management.

## Common Terms

| Term                            | Definition                                                                                                                                                                                                                                                                                   |
| :------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Contributed Funds               | Actual, absolute monetary amounts paid or transferred into the WFU DEAC facility by Reynolda campus faculty or their collaborators. Also, time committments and other efforts expended on behalf of the cluster (as defined and calculated in this policy) are considered contributed funds. |
| Apparent Value                  | Value of a contribution after the initial normalizations and annual time-based devaluations have been applied.                                                                                                                                                                               |
| Individual Contribution         | Sum of all apparent value contributions in a given year.                                                                                                                                                                                                                                     |
| Total Cluster Contributions     | Sum of all **Individual Contributions** from all cluster sources in a given year.                                                                                                                                                                                                            |
| Fair Share Group                | A research group (single PI or group of PIs) contributing apparent value to the cluster in a given year.                                                                                                                                                                                     |
| Individual Fair Share Target    | Percentage of the **Total Cluster Contributions** that an research group contributes through **Individual Contributions** (approximately **Individual Contribution**/**Total Cluster Contributions**).                                                                                       |
| General Group Fair Share Target | Percentage of the **Total Cluster Contributions** that University or Cluster Facility external funding contributes toward the **Total Cluster Contributions**.                                                                                                                               |
| Fund Grace Period               | Period of time after a contribution during which no time-based devaluation occurs to affect the **Apparent Value**.                                                                                                                                                                          |
| Fund Decay Rate                 | Annual rate at which a contribution is devalued after the **Fund Grace Period** expires.                                                                                                                                                                                                     |
|                                 |                                                                                                                                                                                                                                                                                              |



[Category:Cluster](Category:Cluster "wikilink") [Category:
Policy](Category:_Policy "wikilink")---
title: Cluster:Fair Share Policy
permalink: /Cluster:Fair_Share_Policy/
---

