---
title: Mensajes de error en el Diseñador de flujo de trabajo
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- WFDErrorMessages.UI
- System.Activities.Presentation.ErrorActivity.UI
- System.Activities.Presentation.View.ErrorView.UI
ms.assetid: 4d8bbc2e-34fc-477f-9140-4adfd70c34a0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72592d21fdaba1ef47a15a113c820dffe0ba71eb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597053"
---
# <a name="error-messages-in-workflow-designer"></a>Mensajes de error en el Diseñador de flujo de trabajo

En este tema se describen los tipos de mensajes de error que se pueden encontrar al trabajar con Diseñador de flujo de trabajo.

## <a name="situations-in-which-errors-in-the-workflow-designer-occur"></a>Situaciones en las que se producen errores en el Diseñador de flujo de trabajo

Los errores en Diseñador de flujo de trabajo producen en las situaciones siguientes:

1. Hay un error en una expresión.

2. No se han satisfecho las restricciones de validación de una actividad.

3. Hay errores en el archivo XAML que hacen que una actividad no pueda cargarse.

4. Hay errores en el archivo XAML que hacen que el flujo de trabajo no pueda cargarse.

Las expresiones no válidas y las restricciones de validación no satisfechas no impiden la compilación del flujo de trabajo. La compilación del flujo de trabajo se realiza correctamente, pero <xref:System.Activities.InvalidWorkflowException> se produce una excepción en tiempo de ejecución. Si hay errores en el archivo XAML, se produce un error en la compilación.

Dentro de Visual Studio, cuando se carga un flujo de trabajo, sus errores se muestran en el **lista de errores**. Para navegar a la actividad que es el origen del error, haga doble clic en el error en el **lista de errores**.

### <a name="expression-errors"></a>Errores de expresión
 Un círculo rojo con un signo de exclamación junto a la expresión indica que esta no es válida. Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error. Dentro de Visual Studio, haga clic en la expresión para ver la línea que subraya el origen del error. Al mantener el mouse sobre el texto, aparece una información sobre herramientas que describe el origen del error.

### <a name="activity-validation-errors"></a>Errores de validación de actividad
 Cuando no se satisfacen las restricciones de validación de una actividad, aparece un círculo rojo con un signo de exclamación blanco en la esquina superior derecha de la actividad. Al mantener el mouse sobre este icono aparece una información sobre herramientas donde se describe el origen del error.

### <a name="xaml-load-errors"></a>Errores de carga del código XAML
 Cuando se produce un error en la carga de una actividad, aparece un cuadro rojo con el texto "no se pudo cargar la actividad debido a los errores en el código XAML". Esto suele ocurrir cuando el tipo de la actividad no se puede resolver. La actividad no válida se puede eliminar en el diseñador si se selecciona y elimina el cuadro rojo.

### <a name="workflow-load-errors"></a>Errores de carga del flujo de trabajo
 Cuando un flujo de trabajo no se carga, aparece el texto "Diseñador de flujo de trabajo problemas con el documento" en la superficie del diseñador, junto con la información de la excepción que causó el error de carga del flujo de trabajo. Esto se produce normalmente cuando no se puede analizar el archivo de código XAML.
