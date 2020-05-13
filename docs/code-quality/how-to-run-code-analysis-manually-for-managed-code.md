---
title: 'Cómo: Ejecutar el análisis de código manualmente para el código administrado'
ms.date: 11/04/2019
ms.topic: conceptual
helpviewer_keywords:
- code analysis, running
- run code analysis
ms.assetid: 5086d228-f92e-4515-9708-c5b89b9e9a03
author: mavasani
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5fdeb56a0c0f4c5904a00ec53d64dae87aa4e9a5
ms.sourcegitcommit: 92361aac3665a934faa081e1d1ea89a067b01c5b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79431389"
---
# <a name="how-to-run-code-analysis-manually-for-managed-code-requires-visual-studio-2019-version-165-or-later"></a>Cómo: Ejecutar el análisis de código manualmente para código administrado (requiere Visual Studio 2019 versión 16.5 o posterior)
De forma predeterminada, los analizadores de código de .NET Compiler Platform ("Roslyn") analizan el código de Visual Basic o de C. a medida que escribe mediante el análisis en vivo, así como durante la compilación. Por lo tanto, normalmente no sería necesario desencadenar manualmente el análisis de código. Sin embargo, hay algunos escenarios en los que es posible que desee desencadenar manualmente el análisis de código:

- De forma predeterminada, el análisis de código en vivo ejecuta analizadores solo para archivos abiertos en Visual Studio. Sin embargo, es posible que le interese ver advertencias de análisis de código para todos los archivos de un proyecto o solución específicos. Si es así, desea desencadenar el análisis de código una vez en un proyecto o una solución. Como alternativa, puede habilitar el análisis continuo de código en vivo para que se ejecute en toda la solución. Para obtener más información, vea [Cómo: Configurar el ámbito](./configure-live-code-analysis-scope-managed-code.md)de análisis de código en vivo para código administrado .
- Es posible que prefiera el flujo de trabajo de ejecución de análisis de código bajo demanda en lugar del análisis continuo en tiempo de ejecución o el análisis en tiempo de compilación. Si es así, puede deshabilitar la ejecución del analizador durante el análisis en vivo o la compilación. Para obtener información sobre cómo deshabilitar el análisis, consulte Cómo deshabilitar el análisis de [código fuente.](disable-code-analysis.md) A continuación, desea desencadenar manualmente el análisis de código una vez en un proyecto o una solución. 

### <a name="run-code-analysis-manually"></a>Ejecutar análisis de código manualmente

1. En **el Explorador de soluciones**, haga clic en el proyecto.

2. En el menú **Analizar** , haga clic en **Ejecutar análisis de código en** el nombre del *proyecto*.

El análisis de código comenzará a ejecutarse en segundo plano. Debería ver el mensaje Análisis de **código en ejecución para \<el> del proyecto...** en la barra de estado de Visual Studio hacia la esquina inferior izquierda. Una vez completado el análisis de código, el mensaje de estado cambiará a Análisis de código **completado para \<el>del proyecto. ** La lista de errores se actualizará pronto con todos los diagnósticos de análisis de código.
