# Overview {#concept_pqr_4bb_ffb .concept}

Apache Subversion \(SVN\) is an open source version control system that manages timeline-based data changes. This topic describes the terms and operations related to SVN.

## SVN {#section_esy_dcb_ffb .section}

The data that SVN manages is stored in a repository. This repository records all changes of files, so that you can reverse the data to an earlier version or review the change history of files. The terms and operations of SVN are listed as follows:

-   Repository: stores source code.
-   Checkout: checks out source code to a local directory.
-   Commit: commits modified code to the repository.
-   Update: synchronizes source code in the repository to a local directory.

To manage code in SVN, you typically need to perform these steps:

1.  Checkout: Check out source code to a local directory.
2.  Other users modify and commit the source code to the repository.
3.  Update: Obtain the updates of the source code from the repository.
4.  Modify and debug the source code.
5.  Commit: Commit the debugged source code to the repository, so other users can view your modifications.

SVN manages source code by line. When you and other users modify the code in a file at the same time:

-   If the modified code is in different lines, SVN automatically merges the modifications.
-   If the modified code is in the same line, SVN indicates a file conflict. You must confirm the modification manually to resolve the conflict.

## Procedure {#section_zpd_31d_vxl .section}

SVN supports access over HTTP or based on svnserve. You can deploy the access to SVN in these ways:

-   [Deploy access to SVN by using svnserve](intl.en-US/Tutorials/Deploy and use SVN/Deploy access to SVN by using svnserve.md#)
-   [Deploy access to SVN over HTTP](intl.en-US/Tutorials/Deploy and use SVN/Deploy access to SVN over HTTP.md#)

After you deploy SVN, you can commit modifications, obtain updates, and reverse files by using SVN. For more information, see [Use SVN](intl.en-US/Tutorials/Deploy and use SVN/Use SVN.md#).

