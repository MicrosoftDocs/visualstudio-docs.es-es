---
title: 'Cómo: configurar el análisis de código para una aplicación Web ASP.NET | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9b611e303c61e7be9586d6d746e5c859c8dbb5b9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575437"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Cómo: Configurar el análisis de código para una aplicación web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: configurar el análisis de código para una aplicación Web ASP.NET](https://docs.microsoft.com/visualstudio/code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application).  
  
En [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] y [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] puede seleccionar entre una lista de análisis de código *conjuntos de reglas* para aplicar a [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación Web. El conjunto de reglas predeterminado es la reglas recomendadas de Microsoft Mininimum. Puede seleccionar otro conjunto de reglas para aplicar al sitio Web.  
  
### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Para configurar un conjunto de reglas para un proyecto de marco de páginas de ASP.NET  
  
1.  Seleccione el sitio Web en **el Explorador de soluciones**.  
  
2.  En el **analizar** menú, haga clic en **configurar análisis de código para el sitio Web**.  
  
3.  Si ha seleccionado la solución y la solución tiene más de un proyecto, seleccione el sistema de operativo de configuración y de destino de compilación desde el **configuración** y **plataforma** enumera.  
  
4.  Para cada proyecto de la solución, haga clic en el **Pravidel** columna y, a continuación, haga clic en el nombre de la regla de configuración para ejecutar.  
  
5.  De forma predeterminada, el análisis de código se ejecuta en todos los proyectos de la solución. Para deshabilitar o habilitar el análisis de código para un proyecto determinado, siga estos pasos:  
  
    1.  Haga clic en el nombre del proyecto y, a continuación, haga clic en Propiedades.  
  
    2.  Active o desactive el **Habilitar análisis de código** casilla de verificación. También puede ejecutar análisis de código seleccionando **ejecutar análisis de código en el sitio Web** desde el **analizar** menú.  
  
6.  En el **ejecutar este conjunto de reglas** desplegable lista, siga estos pasos:  
  
    -   Seleccione el conjunto de reglas que desea usar.  
  
    -   Seleccione  **\<examinar >** especificar una regla personalizada existente conjunto que no está en la lista.  
  
    -   Defina un conjunto de reglas personalizado. Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).



