---
title: "C&#243;mo: Configurar el an&#225;lisis de c&#243;digo para un proyecto de c&#243;digo administrado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.csvb"
helpviewer_keywords: 
  - "análisis de código, selección de conjuntos de reglas"
  - "análisis de código, conjuntos de reglas"
ms.assetid: 618f6ff3-db0e-46cb-b08d-dfa35e62c9e7
caps.latest.revision: 33
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 33
---
# C&#243;mo: Configurar el an&#225;lisis de c&#243;digo para un proyecto de c&#243;digo administrado
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] y [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], puede elegir en una lista de *conjuntos de reglas* de análisis de código para aplicarlas a un proyecto de código administrado.  El conjunto de reglas predeterminado es Reglas mínimas recomendadas de Microsoft.  Puede aplicar otro conjunto de reglas a un proyecto o a todos los proyectos de una solución.  
  
> [!NOTE]
>  Para obtener información sobre cómo configurar un conjunto de reglas para las aplicaciones web ASP.NET, vea [Cómo: Configurar el análisis de código para una aplicación web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
### Para configurar un conjunto de reglas para un proyecto de .NET Framework  
  
1.  En el **Explorador de soluciones**, haga clic en el proyecto.  
  
2.  En el menú **Analizar**, haga clic en **Configurar el análisis de código para** *ProjectName*.  
  
3.  En las listas **Configuración** y **Plataforma**, haga clic en la configuración de compilación y la plataforma de destino.  
  
4.  Para ejecutar el análisis de código cada vez que se compila el proyecto con la configuración seleccionada, active la casilla **Habilitar análisis de código al compilar \(define la constante CODE\_ANALYSIS\)**.  También puede ejecutar el análisis de código de forma manual si abre el menú **Analizar** y hace clic en **Ejecutar análisis de código en** *ProjectName*.  
  
5.  De forma predeterminada, el análisis de código no notifica las advertencias de código generadas automáticamente por herramientas externas.  Para ver las advertencias del código generado, desactive la casilla **Suprimir resultados del código generado**.  
  
    > [!NOTE]
    >  Esta opción no suprime los errores ni las advertencias del análisis de código generado cuando aparecen en formularios y plantillas.  Puede ver y mantener el código fuente de un formulario o una plantilla.  
  
6.  En la lista **Ejecutar este conjunto de reglas**, realice uno de los siguientes procedimientos:  
  
    -   Haga clic en el conjunto de reglas que desee utilizar.  
  
    -   Haga clic en **\<Examinar...\>** para especificar un conjunto de reglas personalizado existente que no esté en la lista.  
  
    -   Defina un conjunto de reglas personalizado.  
  
         Para obtener más información, vea [Crear conjuntos de reglas personalizadas](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## Vea también  
 [Tutorial: Configurar y utilizar un conjunto de reglas personalizado](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)