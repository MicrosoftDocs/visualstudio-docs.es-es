---
title: "C&#243;mo: Configurar el an&#225;lisis de c&#243;digo para una aplicaci&#243;n web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Configurar el an&#225;lisis de c&#243;digo para una aplicaci&#243;n web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] y [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], puede seleccionar en una lista de *conjuntos de reglas* de análisis de código para aplicarlos a una aplicación web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  El conjunto de reglas predeterminado es Reglas mínimas recomendadas de Microsoft.  Puede seleccionar otro conjunto de reglas para aplicarlo al sitio web.  
  
### Para configurar un conjunto de reglas para un proyecto de marco de páginas de ASP.NET  
  
1.  Seleccione el sitio web en el **Explorador de soluciones**.  
  
2.  En el menú **Analizar**, haga clic en **Configurar análisis de código para sitio web**.  
  
3.  Si seleccionó la solución y esta tiene más de un proyecto, seleccione la configuración de compilación y el sistema operativo de destino en las listas **Configuración** y **Plataforma**.  
  
4.  Para cada proyecto de la solución, haga clic en la columna **Conjunto de reglas** y, a continuación, haga clic en el nombre del conjunto de reglas que se va a ejecutar.  
  
5.  De forma predeterminada, el análisis de código se ejecuta en todos los proyectos de la solución.  Para deshabilitar o habilitar el análisis de código para un proyecto determinado, siga estos pasos:  
  
    1.  Haga clic con el botón secundario en el nombre del proyecto y, a continuación, haga clic en Propiedades.  
  
    2.  Active o desactive la casilla **Habilitar análisis de código**.  También puede ejecutar el análisis de código manualmente seleccionando **Ejecutar análisis de código en el sitio web** desde el menú **Analizar**.  
  
6.  En la lista desplegable **Ejecutar este conjunto de reglas**, siga estos pasos:  
  
    -   Seleccione el conjunto de reglas que desee utilizar.  
  
    -   **\<Browse\>** Seleccione para especificar un conjunto de reglas personalizado existente que no está en la lista.  
  
    -   Defina un conjunto de reglas personalizado.  Para obtener más información, vea [Crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).