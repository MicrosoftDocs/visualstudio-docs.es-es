---
title: 'Cómo: configurar el análisis de código para un proyecto de código administrado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1ac04a3d8834e3fc24f148fc36327d101e43720a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658857"
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Cómo: Configurar el análisis de código para un proyecto de código administrado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] y [!INCLUDE[vsPro](../includes/vspro-md.md)], puede elegir en una lista de *conjuntos de reglas* de análisis de código para aplicarlos a un proyecto de código administrado. El conjunto de reglas predeterminado es Reglas mínimas recomendadas de Microsoft. Puede aplicar otro conjunto de reglas a un proyecto o a todos los proyectos de una solución.

> [!NOTE]
> Para obtener información sobre cómo configurar un conjunto de reglas para las aplicaciones Web de ASP.NET, consulte [Cómo: configurar el análisis de código para una aplicación Web de ASP.net](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Para configurar un conjunto de reglas para un proyecto de .NET Framework

1. En **Explorador de soluciones**, haga clic en el proyecto.

2. En el menú **analizar** , haga clic en **configurar análisis de código para** *projectname*.

3. En las listas **configuración** y **plataforma** , haga clic en la configuración de compilación y la plataforma de destino.

4. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, active la casilla **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** . También puede ejecutar el análisis de código manualmente abriendo el menú **analizar** y haciendo clic en **Ejecutar Análisis de código en** *projectname*.

5. De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas. Para ver las advertencias del código generado, desactive la casilla **suprimir resultados de código generado** .

    > [!NOTE]
    > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.

6. En la lista **ejecutar este conjunto de reglas** , realice una de las acciones siguientes:

    - Haga clic en el conjunto de reglas que desee utilizar.

    - Haga clic en **\<Browse... >** para especificar un conjunto de reglas personalizado existente que no está en la lista.

    - Defina un conjunto de reglas personalizado.

         Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Vea también
 [Tutorial: Configurar y usar un conjunto de reglas personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
