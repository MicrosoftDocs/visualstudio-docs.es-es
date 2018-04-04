---
title: 'Cómo: configurar el análisis de código para un proyecto de código administrado | Documentos de Microsoft'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 46d41b09f0f6639195613c8a4d9a08f952c79525
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Cómo: Configurar el análisis de código para un proyecto de código administrado

En Visual Studio, puede elegir entre una lista de análisis de código *conjuntos de reglas* para aplicarlas a un proyecto de código administrado. El conjunto de reglas predeterminado es *reglas mínimas recomendadas de Microsoft*. Puede aplicar otro conjunto de reglas a un proyecto o a todos los proyectos de una solución.

> [!TIP]
> Para obtener información sobre cómo configurar un conjunto de reglas para aplicaciones Web ASP.NET, vea [Cómo: configurar el análisis de código para una aplicación Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Para configurar un conjunto de reglas para un proyecto de .NET Framework

1. Abra la **análisis de código** ficha en páginas de propiedades del proyecto. Puede hacerlo en cualquiera de las maneras siguientes:

   - En **el Explorador de soluciones**, seleccione el proyecto. En la barra de menús, seleccione **analizar** > **configurar análisis de código** > **para \<NombreDeProyecto >**.

   - Haga clic en el proyecto en **el Explorador de soluciones** y seleccione **propiedades**y, a continuación, seleccione la **análisis de código** ficha.

1. En el **configuración** y **plataforma** listas, seleccione la plataforma de destino y la configuración de compilación.

1. Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, seleccione la **Habilitar análisis de código al compilar** casilla de verificación. También puede ejecutar análisis de código seleccionando **analizar** > **ejecutar análisis de código** > **ejecutar análisis de código en \<NombreDeProyecto >**.

1. De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas. Para ver las advertencias del código generado, desactive el **Suprimir resultados del código generado** casilla de verificación.

    > [!NOTE]
    > Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas. Puede ver y mantener el código fuente de un formulario o una plantilla, sin necesidad de que se sobrescribe.

1. En el **ejecutar este conjunto de reglas** lista, realice una de las siguientes acciones:

    - Seleccione el conjunto de reglas que desea utilizar.

    - Seleccione  **\<Examinar... >** encontrar una regla personalizada existente establece que no está en la lista.

    - Defina un conjunto de reglas personalizado. Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Vea también

- [Tutorial: Configurar y usar un conjunto de reglas personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
- [Cómo: Configurar el análisis de código para una aplicación web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)