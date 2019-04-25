---
title: Mensajes de error en el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab2cb4562f816b254b658cfdc152dc38033fbe03
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60104550"
---
# <a name="error-messages-in-workflow-designer"></a>Mensajes de error en el Diseñador de flujo de trabajo

En este tema se describe los tipos de mensajes de error que se pueden encontrar al trabajar con el Diseñador de flujo de trabajo.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situaciones en las que se producen errores en el Diseñador de flujo de trabajo

Se producen errores en el Diseñador de flujo de trabajo en las situaciones siguientes:

1. Hay un error en una expresión.

2. No se han satisfecho las restricciones de validación de una actividad.

3. Hay errores en el archivo XAML que hacen que una actividad no pueda cargarse.

4. Hay errores en el archivo XAML que hacen que el flujo de trabajo no pueda cargarse.

Las expresiones no válidas y las restricciones de validación no satisfechas no impiden la compilación del flujo de trabajo. La compilación del flujo de trabajo se ha realizado correctamente, pero se produce <xref:System.Activities.InvalidWorkflowException> en tiempo de ejecución. Si hay errores en el archivo XAML, se produce un error en la compilación.

Dentro de Visual Studio, cuando se carga un flujo de trabajo, los errores se muestran en el **lista de errores**. Para navegar a la actividad que es el origen del error, haga doble clic en el error en la **lista de errores**.

### <a name="expression-errors"></a>Errores de expresión
 Un círculo rojo con un signo de exclamación junto a la expresión indica que esta no es válida. Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error. Dentro de Visual Studio, haga clic en la expresión para ver la línea que subraya el origen del error. Al mantener el mouse sobre el texto, aparece una información sobre herramientas que describe el origen del error.

### <a name="activity-validation-errors"></a>Errores de validación de actividad
 Cuando no se satisfacen las restricciones de validación de una actividad, aparece un círculo rojo con un signo de exclamación blanco en la esquina superior derecha de la actividad. Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error.

### <a name="xaml-load-errors"></a>Errores de carga del código XAML
 Cuando una actividad no se carga, aparece un cuadro rojo con el texto "no se cargó la actividad debido a errores en el XAML". Esto suele ocurrir cuando no se puede resolver el tipo de la actividad. La actividad no válida se puede eliminar en el diseñador si se selecciona y elimina el cuadro rojo.

### <a name="workflow-load-errors"></a>Errores de carga del flujo de trabajo
 Cuando no se puede cargar un flujo de trabajo, el texto "Problemas de diseñador de flujo de trabajo ha encontrado con el documento" aparece en la superficie del diseñador, junto con la información de excepción que produjo el error del flujo de trabajo cargar. Esto se produce normalmente cuando no se puede analizar el archivo de código XAML.