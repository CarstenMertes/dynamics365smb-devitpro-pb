---
title: AVS Error AVS0006
description: "The runtime version '{0}' is not supported for the release '{1}' because its latest supported runtime version is '{2}'."
ms.author: thpeder
ms.date: 01/30/2025
ms.reviewer: solsen
ms.topic: reference
author: thpeder
---

# AVS Error AVS0006

[!INCLUDE[banner_preview](../includes/banner_preview.md)]

The runtime version '{0}' is not supported for the release '{1}' because its latest supported runtime version is '{2}'.

## How to fix this diagnostic?

In the app.json file of the app you have to specify the latest supported runtime version or lower. For more information, see [app.json file](../devenv-json-files.md#appjson-file) and [Choosing Runtime Version in AL](../devenv-choosing-runtime.md).

## Related information

[Get started with AL](../devenv-get-started.md)  
[Developing Extensions](../devenv-dev-overview.md)  
