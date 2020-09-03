---
title: 'Cómo: configurar el análisis de código para una aplicación Web de ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.asp
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 423264362118343d573b417cd055d2d722df995e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657463"
---
# <a name="how-to-configure-code-analysis-for-an-aspnet-web-application"></a>Cómo: Configurar el análisis de código para una aplicación web ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] y [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] puede seleccionar en una lista de *conjuntos de reglas* de análisis de código para aplicarlos a la [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicación Web. El conjunto de reglas predeterminado es las reglas recomendadas de Microsoft Mininimum. Puede seleccionar otro conjunto de reglas para aplicar al sitio Web.

### <a name="to-configure-a-rule-set-for-an-aspnet-page-framework-project"></a>Para configurar un conjunto de reglas para un proyecto de marco de páginas de ASP.NET

1. Seleccione el sitio web en **Explorador de soluciones**.

2. En el menú **analizar** , haga clic en **configurar análisis de código para el sitio web**.

3. Si seleccionó la solución y la solución tiene más de un proyecto, seleccione la configuración de compilación y el sistema operativo de destino en las listas **configuración** y **plataforma** .

4. Para cada proyecto de la solución, haga clic en la columna **conjunto de reglas** y, a continuación, haga clic en el nombre del conjunto de reglas que se va a ejecutar.

5. De forma predeterminada, el análisis de código se ejecuta en todos los proyectos de la solución. Para deshabilitar o habilitar el análisis de código para un proyecto determinado, siga estos pasos:

    1. Haga clic con el botón secundario en el nombre del proyecto y seleccione Propiedades.

    2. Active o desactive la casilla **Habilitar análisis de código** . También puede ejecutar el análisis de código manualmente seleccionando **Ejecutar Análisis de código en el sitio web** en el menú **analizar** .

6. En la lista desplegable **ejecutar este conjunto de reglas** , siga estos pasos:

    - Seleccione el conjunto de reglas que desea usar.

    - Seleccione esta **\<Browse>** configuración para especificar un conjunto de reglas personalizado existente que no esté en la lista.

    - Defina un conjunto de reglas personalizado. Para obtener más información, consulte [crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).
