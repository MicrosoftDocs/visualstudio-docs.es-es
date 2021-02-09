---
title: 'Diseñador de flujo de trabajo: Cómo usar el diseñador de variables'
description: Obtenga información sobre cómo puede usar el diseñador de variables para crear variables para su uso en escenarios de enlace de datos e instrucciones condicionales.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a427b14db5be8081352ce54bf13900fa826202b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894015"
---
# <a name="how-to-use-the-variable-designer"></a>Utilizar el diseñador de variables

El diseñador variables se utiliza para crear variables con el fin de utilizarlas en escenarios de enlace de datos e instrucciones condicionales. Se tiene acceso al diseñador haciendo clic en el botón **variables** en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de variables que aparecen en un formulario tabular y se pueden ordenar por cada uno de los encabezados de columna, excepto por la columna **predeterminada** . Cada variable contiene un nombre, tipo de variable, ámbito y valor predeterminado (en su caso). El nombre y valor predeterminado son campos de texto editable, y el tipo y ámbito son listas desplegables. El ámbito es la actividad que se seleccionó cuando se invocó el diseñador de variables. Si no se puede crear una variable en el ámbito de la selección, el ámbito tendrá como valor predeterminado la actividad antecesora más próxima de la selección que permita la creación de variables en su ámbito. Para obtener más información, vea [variables y argumentos (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 El criterio de ordenación no se aplica hasta que el usuario utilice explícitamente uno de los controles de ordenación, cierre y vuelva a abrir el diseñador de variables o bien, cree otra variable.

## <a name="to-create-a-new-variable"></a>Para crear una nueva variable

1. Abra una solución de flujo de trabajo o actividad en Visual Studio.

2. En el lienzo de diseño, seleccione una actividad en su flujo de trabajo.

3. Abra el diseñador de variables haciendo clic en el botón **variables** en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de variables.

4. Haga clic en la fila vacía con la etiqueta **crear variable**. Esto agregará una nueva fila con una nueva variable con los siguientes valores predeterminados: variablex para el **nombre** , donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de variable únicos, una **cadena** para el **tipo de variable** y una **secuencia** para el **ámbito**. No se agrega ningún valor para el valor **predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.

    > [!NOTE]
    > Para eliminar una variable, seleccione la variable haciendo clic en ella y, a continuación, presione la tecla **Supr** .

## <a name="see-also"></a>Vea también

- [Usar el Diseñador de flujo de trabajo](developing-applications-with-the-workflow-designer.md)
- [Variables y argumentos](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Cómo: Usar el diseñador de argumentos](../workflow-designer/how-to-use-the-argument-designer.md)
