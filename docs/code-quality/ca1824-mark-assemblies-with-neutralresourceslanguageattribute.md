---
title: "CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1824"
  - "MarkAssembliesWithNeutralResourcesLanguage"
helpviewer_keywords: 
  - "MarkAssembliesWithNeutralResourcesLanguage"
  - "CA1824"
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA1824: Marque los ensamblados con NeutralResourcesLanguageAttribute
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|  
|Identificador de comprobación|CA1824|  
|Categoría|Microsoft.Performance|  
|Cambio problemático|Poco problemático|  
  
## Motivo  
 Un ensamblado contiene un recurso basado en **ResX** pero no tiene <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> aplicado a él.  
  
## Descripción de la regla  
 El atributo **NeutralResourcesLanguage** informa a **ResourceManager** del idioma utilizado para mostrar los recursos de la referencia cultural neutral de un ensamblado.  Cuando busca recursos en la misma referencia cultural que el idioma de recursos neutrales, **ResourceManager** utiliza automáticamente los recursos ubicados en el ensamblado principal,  en lugar de buscar un ensamblado satélite que tenga la referencia cultural de la interfaz de usuario actual para el subproceso actual.  Esto mejora el rendimiento de la búsqueda del primer recurso que se carga y puede reducir el espacio de trabajo.  
  
## Corregir las infracciones  
 Para corregir una infracción de esta regla, agregue el atributo al ensamblado, y especifique el idioma de los recursos de la referencia cultural neutral.  
  
## Especificar el lenguaje  
  
#### Para especificar el lenguaje del recurso de la referencia cultural neutral  
  
1.  En el **Explorador de soluciones**, haga clic con el botón secundario del mouse en el proyecto y, a continuación, haga clic en **Propiedades**.  
  
2.  En la barra de navegación izquierda, seleccione **Aplicación** y, a continuación, haga clic en **Información de ensamblado**.  
  
3.  En el cuadro de diálogo **Información de ensamblado**, seleccione el lenguaje en la lista desplegable **Idioma neutro**.  
  
4.  Haga clic en **Aceptar**.  
  
## Cuándo suprimir advertencias  
 Se puede suprimir una advertencia de esta regla.  Sin embargo, el rendimiento de inicio podría reducirse.