---
title: Cómo ejecutar el análisis de código manualmente para .NET
ms.date: 09/02/2020
description: Obtenga información sobre cómo ejecutar manualmente el análisis de código en la versión 16,5 de Visual Studio 2019 o versiones posteriores. Vea cómo ejecutar analizadores de Roslyn en código C# o Visual Basic.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 2eb4beff76d602bb4ce6182fab6091c7cd2a0096
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348728"
---
# <a name="run-code-analysis-manually-for-net"></a>Ejecutar el análisis de código manualmente para .NET
De forma predeterminada, los analizadores de .NET Compiler Platform ("Roslyn") analizan el código de C# o Visual Basic mientras escribe realizando el análisis en directo, así como durante la compilación. Por lo tanto, normalmente no necesitaría activar manualmente el análisis de código. Sin embargo, hay algunos escenarios en los que puede que desee activar manualmente el análisis de código:

> [!NOTE]
> Ejecutar el análisis de código manualmente requiere Visual Studio 2019 versión 16,5 o posterior.

- De forma predeterminada, el análisis de código activo ejecuta analizadores solo para archivos abiertos en Visual Studio. Sin embargo, puede que le interese ver las advertencias de análisis de código de todos los archivos de un proyecto o una solución concretos. Si es así, desea desencadenar el análisis de código una vez en un proyecto o una solución. Como alternativa, puede habilitar el análisis de código activo continuo para que se ejecute en toda la solución. Para obtener más información, vea [Cómo: Configurar el ámbito del análisis activo para el código administrado](./configure-live-code-analysis-scope-managed-code.md).
- Puede preferir el flujo de trabajo de ejecución de análisis de código a petición sobre el análisis activo continuo o el análisis en tiempo de compilación. Si es así, puede deshabilitar la ejecución del analizador durante el análisis o la compilación en vivo. Para obtener información sobre cómo deshabilitar el análisis, vea [cómo deshabilitar el análisis de código fuente](disable-code-analysis.md). Después, querrá desencadenar manualmente el análisis de código una vez en un proyecto o una solución.

### <a name="run-code-analysis-manually"></a>Ejecutar análisis de código manualmente

1. En **Explorador de soluciones** , seleccione el proyecto.

2. En el menú **analizar** , seleccione **Ejecutar Análisis de código en** *nombre del proyecto*.

El análisis de código comenzará a ejecutarse en segundo plano. Debería ver el mensaje **ejecutando análisis de código para \<project> ...** en la barra de estado de Visual Studio hacia la esquina inferior izquierda. Una vez que se completa el análisis de código, el mensaje de estado cambiará al **análisis de código completado para \<project>**. La lista de errores se actualizará pronto con todos los diagnósticos de análisis de código.
