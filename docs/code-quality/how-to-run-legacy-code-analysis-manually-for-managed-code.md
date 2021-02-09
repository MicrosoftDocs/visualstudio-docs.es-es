---
title: Ejecutar el análisis de código heredado manualmente (.NET)
description: Obtenga información sobre cómo detectar posibles defectos en el código fuente. Vea cómo ejecutar el análisis de código heredado manualmente en código administrado en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: Mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 45f201e2c647a1b1074585d59c7618e1ddeb9084
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860001"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Cómo: ejecutar el análisis de código heredado manualmente para código administrado

La herramienta de análisis de código proporciona información sobre los posibles defectos en el código fuente. Puede ejecutar el análisis de código automáticamente con cada compilación de un proyecto de código y también puede ejecutar el análisis de código manualmente. Las reglas que se comprueban cuando se ejecuta el análisis de código se especifican en la página Análisis de código de las páginas de propiedades del proyecto. Para obtener más información, vea [Cómo: configurar el análisis de código para un proyecto de código administrado](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md).

## <a name="to-run-code-analysis-manually"></a>Para ejecutar el análisis de código manualmente

1. Si está en Visual Studio 2019 versión 16,5 o posterior, ejecute el siguiente comando en el símbolo del sistema antes de iniciar Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. En **Explorador de soluciones**, haga clic en el proyecto.

3. En el menú **analizar** , haga clic en **Ejecutar Análisis de código en** *nombre del proyecto*.
