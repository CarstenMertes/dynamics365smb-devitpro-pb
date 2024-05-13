---
title: "Add a test app"
description: "Adding a test app to your AL-Go solution for Business Central."
author: freddyk
ms.custom: na
ms.date: 12/30/2021
ms.reviewer: solsen
ms.topic: conceptual
ms.service: dynamics-365-business-central
ms.author: solsen
---

# Add a test app

> *The prerequisite for this how to is that you have completed the [Create a new per-tenant extension and start developing in Visual Studio Code](algo-get-started.md) instructions*.

## Steps

1. On www.github.com, for your previously created solution, go to the **Actions** tab.
1. In the left pane, select the **Create a new test app** workflow, and then choose the **Run workflow** button.
1. In the dialog, enter values for name, publisher, and ID range. In the **DIRECT COMMIT** field, keep **N** for no and then choose **Run workflow**.
1. When the workflow has completed, navigate to the **Pull requests** tab, inspect the pull request, and then **Merge** the pull request.
1. Now, go to the **Actions** tab and you see that a **Merge pull request** CI workflow has been started.  
This workflow will at some point fail. If you inspect the build, you see the details of the error.
1. To fix the error, open Visual Studio Code, and pull changes from the server by using the sync button, open the `HelloWorld.Test.al` file and fix the test message.
1. Now, stage, commit, and push the change. On www.github.com, in the **Actions** tab, you see that your check-in caused another CI workflow to be kicked off.  
This time it should be passing and if you investigate the CI/CD workflow, you see that the deploy step has been skipped as no environment existed.


## Next step

Now, a next step to take, could be [Register a Customer Sandbox Environment for Continuous Deployment using S2S](algo-register-sandbox-env.md). 

## See also

[AL-Go Overview](algo-overview.md)  
[Get Started](algo-get-started.md)  
[Register a Customer Sandbox Environment for Continuous Deployment using S2S Authentication](algo-register-sandbox-env.md)