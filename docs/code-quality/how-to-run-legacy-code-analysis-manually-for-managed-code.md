---
title: 'Cómo: Ejecutar el análisis de código heredado manualmente para el código administrado'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9d2693bcff8e83839b4171bae60b138c967f10e5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79432088"
---
# <a name="how-to-run-legacy-code-analysis-manually-for-managed-code"></a>Cómo: Ejecutar el análisis de código heredado manualmente para el código administrado
La herramienta de análisis de código le proporciona información sobre posibles defectos en el código fuente. Puede ejecutar el análisis de código automáticamente con cada compilación de un proyecto de código y también puede ejecutar el análisis de código manualmente. Las reglas que se comprueban cuando se ejecuta el análisis de código se especifican en la página Análisis de código de las páginas de propiedades del proyecto. Para obtener más información, vea [Cómo: Configurar](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)el análisis de código para un proyecto de código administrado .

## <a name="to-run-code-analysis-manually"></a>Para ejecutar el análisis de código manualmente

1. Si está en Visual Studio 2019 versión 16.5 o posterior, ejecute el siguiente comando en el símbolo del sistema antes de iniciar Visual Studio:

```
set EnableLegacyCodeAnalysis = true
```

2. En **el Explorador de soluciones**, haga clic en el proyecto.

3. En el menú **Analizar** , haga clic en **Ejecutar análisis de código en** el nombre del *proyecto*.

