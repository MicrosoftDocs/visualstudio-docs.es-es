---
title: "Cómo: configurar el análisis de código para un proyecto de código administrado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d62957a75c844d736a1168010616d5cf2c795bee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Cómo: Configurar el análisis de código para un proyecto de código administrado
En [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] y [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], puede elegir entre una lista de análisis de código *conjuntos de reglas* para aplicarlas a un proyecto de código administrado. El conjunto de reglas predeterminado es Reglas mínimas recomendadas de Microsoft. Puede aplicar otro conjunto de reglas a un proyecto o a todos los proyectos de una solución.  
  
> [!NOTE]
>  Para obtener información sobre cómo configurar un conjunto de reglas para aplicaciones Web ASP.NET, vea [Cómo: configurar el análisis de código para una aplicación Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Para configurar un conjunto de reglas para un proyecto de .NET Framework  
  
1.  En **el Explorador de soluciones**, haga clic en el proyecto.  
  
2.  En el **analizar** menú, haga clic en **configurar análisis de código para** *ProjectName*.  
  
3.  En el **configuración** y **plataforma** listas, haga clic en la plataforma de destino y la configuración de compilación.  
  
4.  Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione la **Habilitar análisis de código al compilar (define la constante CODE_ANALYSIS)** casilla de verificación. También puede ejecutar análisis de código, abra el **analizar** menú y haga clic en **ejecutar análisis de código en** *ProjectName*.  
  
5.  De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas. Para ver las advertencias del código generado, desactive el **Suprimir resultados del código generado** casilla de verificación.  
  
    > [!NOTE]
    >  Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla.  
  
6.  En el **ejecutar este conjunto de reglas** lista, realice una de las siguientes acciones:  
  
    -   Haga clic en el conjunto de reglas que desee utilizar.  
  
    -   Haga clic en  **\<Examinar... >** especificar una regla personalizada existente conjunto que no está en la lista.  
  
    -   Defina un conjunto de reglas personalizado.  
  
         Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Configurar y usar un conjunto de reglas personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)