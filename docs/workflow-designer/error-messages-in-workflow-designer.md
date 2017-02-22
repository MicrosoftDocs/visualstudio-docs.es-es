---
title: "Mensajes de error en el Dise&#241;ador de flujo de trabajo | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "WFDErrorMessages.UI"
  - "System.Activities.Presentation.ErrorActivity.UI"
  - "System.Activities.Presentation.View.ErrorView.UI"
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Mensajes de error en el Dise&#241;ador de flujo de trabajo
Este tema describe los tipos de mensaje de error que se pueden encontrar al trabajar con [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)].  
  
## Situaciones en las que se producen errores en el Diseñador de flujo de trabajo  
 Los errores en [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] se producen en las situaciones siguientes:  
  
1.  Hay un error en una expresión.  
  
2.  No se han satisfecho las restricciones de validación de una actividad.  
  
3.  Hay errores en el archivo XAML que hacen que una actividad no pueda cargarse.  
  
4.  Hay errores en el archivo XAML que hacen que el flujo de trabajo no pueda cargarse.  
  
 Las expresiones no válidas y las restricciones de validación no satisfechas no impiden la compilación del flujo de trabajo.La compilación del flujo de trabajo se ha realizado correctamente, pero se produce <xref:System.Activities.InvalidWorkflowException> en tiempo de ejecución.Si hay errores en el archivo XAML, se produce un error en la compilación.  
  
 En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], cuando se carga un flujo de trabajo, los errores se muestran en la **Lista de errores**.Para desplazarse hasta la actividad que es el origen del error, haga doble clic en el error en la **Lista de errores**.  
  
### Errores de expresión  
 Un círculo rojo con un signo de exclamación junto a la expresión indica que esta no es válida.Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error.En [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], haga clic en la expresión para ver la línea que subraya el origen del error.Al mantener el mouse sobre el texto, aparece una información sobre herramientas que describe el origen del error.  
  
### Errores de validación de actividad  
 Cuando no se satisfacen las restricciones de validación de una actividad, aparece un círculo rojo con un signo de exclamación blanco en la esquina superior derecha de la actividad.Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error.  
  
### Errores de carga del código XAML  
 Cuando no se carga una actividad, aparece un cuadro rojo con el texto "No se cargó la actividad debido a los errores en el código XAML".Esto se produce normalmente cuando no se puede resolver el tipo de la actividad.La actividad no válida se puede eliminar en el diseñador si se selecciona y elimina el cuadro rojo.  
  
### Errores de carga del flujo de trabajo  
 Cuando no se carga un flujo de trabajo, aparece el texto "Problemas del Diseñador de flujo de trabajo con el documento" en la superficie del diseñador, junto con la información sobre la excepción que hizo que se produjera un error en la carga del flujo de trabajo.Esto se produce normalmente cuando no se puede analizar el archivo de código XAML.