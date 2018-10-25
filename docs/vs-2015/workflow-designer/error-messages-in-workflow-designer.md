---
title: Mensajes de error en el Diseñador de flujo de trabajo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: efd6bc680be42f1074da8d2313b1a4b8e9307580
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894851"
---
# <a name="error-messages-in-workflow-designer"></a>Mensajes de error en el Diseñador de flujo de trabajo
Este tema describe los tipos de mensaje de error que se pueden encontrar al trabajar con [!INCLUDE[wfd1](../includes/wfd1-md.md)].  
  
## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situaciones en las que se producen errores en el Diseñador de flujo de trabajo  
 Los errores en [!INCLUDE[wfd2](../includes/wfd2-md.md)] se producen en las situaciones siguientes:  
  
1. Hay un error en una expresión.  
  
2. No se han satisfecho las restricciones de validación de una actividad.  
  
3. Hay errores en el archivo XAML que hacen que una actividad no pueda cargarse.  
  
4. Hay errores en el archivo XAML que hacen que el flujo de trabajo no pueda cargarse.  
  
   Las expresiones no válidas y las restricciones de validación no satisfechas no impiden la compilación del flujo de trabajo. La compilación del flujo de trabajo se ha realizado correctamente, pero se produce <xref:System.Activities.InvalidWorkflowException> en tiempo de ejecución. Si hay errores en el archivo XAML, se produce un error en la compilación.  
  
   Dentro de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], cuando se carga un flujo de trabajo, los errores se muestran en el **lista de errores**. Para navegar a la actividad que es el origen del error, haga doble clic en el error en la **lista de errores**.  
  
### <a name="expression-errors"></a>Errores de expresión  
 Un círculo rojo con un signo de exclamación junto a la expresión indica que esta no es válida. Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error. En [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], haga clic en la expresión para ver la línea que subraya el origen del error. Al mantener el mouse sobre el texto, aparece una información sobre herramientas que describe el origen del error.  
  
### <a name="activity-validation-errors"></a>Errores de validación de actividad  
 Cuando no se satisfacen las restricciones de validación de una actividad, aparece un círculo rojo con un signo de exclamación blanco en la esquina superior derecha de la actividad. Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error.  
  
### <a name="xaml-load-errors"></a>Errores de carga del código XAML  
 Cuando no se carga una actividad, aparece un cuadro rojo con el texto "No se cargó la actividad debido a los errores en el código XAML". Esto se produce normalmente cuando no se puede resolver el tipo de la actividad. La actividad no válida se puede eliminar en el diseñador si se selecciona y elimina el cuadro rojo.  
  
### <a name="workflow-load-errors"></a>Errores de carga del flujo de trabajo  
 Cuando no se carga un flujo de trabajo, aparece el texto "Problemas del Diseñador de flujo de trabajo con el documento" en la superficie del diseñador, junto con la información sobre la excepción que hizo que se produjera un error en la carga del flujo de trabajo. Esto se produce normalmente cuando no se puede analizar el archivo de código XAML.