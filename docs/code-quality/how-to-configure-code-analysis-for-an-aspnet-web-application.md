---
title: "Cómo: configurar el análisis de código para una aplicación Web ASP.NET | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: "13"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: aspnet
ms.openlocfilehash: 51ece959ad0c33c4676e81203cacc025d9ef2884
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Cómo: Configurar el análisis de código para una aplicación web ASP.NET
En [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] y [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] puede seleccionar de una lista de análisis de código *conjuntos de reglas* para aplicar a [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicación Web. El conjunto de reglas predeterminado es reglas de recomendadas Mininimum de Microsoft. Puede seleccionar otro conjunto de reglas para aplicar al sitio Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Para configurar un conjunto de reglas para un proyecto de marco de páginas de ASP.NET  
  
1.  Seleccione el sitio Web en **el Explorador de soluciones**.  
  
2.  En el **analizar** menú, haga clic en **configurar análisis de código para el sitio Web**.  
  
3.  Si seleccionó la solución y la solución tiene más de un proyecto, seleccione el sistema de operativo de destino y la configuración de compilación de la **configuración** y **plataforma** enumera.  
  
4.  Para cada proyecto de la solución, haga clic en el **conjunto de reglas** columna y, a continuación, haga clic en el nombre de la regla configurado para ejecutarse.  
  
5.  De forma predeterminada, el análisis de código se ejecuta en todos los proyectos de la solución. Para deshabilitar o habilitar el análisis de código para un proyecto determinado, siga estos pasos:  
  
    1.  Haga clic en el nombre del proyecto y, a continuación, haga clic en Propiedades.  
  
    2.  Active o desactive el **Habilitar análisis de código** casilla de verificación. También puede ejecutar análisis de código seleccionando **ejecutar análisis de código en el sitio Web** desde el **analizar** menú.  
  
6.  En el **ejecutar este conjunto de reglas** lista desplegable lista, siga estos pasos:  
  
    -   Seleccione el conjunto de reglas que desea utilizar.  
  
    -   Seleccione  **\<examinar >** especificar una regla personalizada existente conjunto que no está en la lista.  
  
    -   Defina un conjunto de reglas personalizado. Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).