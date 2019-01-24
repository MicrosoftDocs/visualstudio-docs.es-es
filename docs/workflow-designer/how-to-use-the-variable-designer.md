---
title: 'Diseñador de flujo de trabajo - Cómo: Usar el diseñador de variables'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b7df8f03444a0205c5628bbd36f249d68b43ad7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824346"
---
# <a name="how-to-use-the-variable-designer"></a>Procedimiento Usar el diseñador de variables

El diseñador variables se utiliza para crear variables con el fin de utilizarlas en escenarios de enlace de datos e instrucciones condicionales. El diseñador se tiene acceso haciendo clic en el **Variables** situado en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de variables que aparecen en un formato tabular y se pueden ordenar por cada uno de los encabezados de columna, excepto para el **predeterminado** columna. Cada variable contiene un nombre, tipo de variable, ámbito y valor predeterminado (en su caso). El nombre y valor predeterminado son campos de texto editable, y el tipo y ámbito son listas desplegables. El ámbito es la actividad que se seleccionó cuando se invocó el diseñador de variables. Si no se puede crear una variable en el ámbito de la selección, el ámbito tendrá como valor predeterminado la actividad antecesora más próxima de la selección que permita la creación de variables en su ámbito. Para obtener más información, consulte [Variables y argumentos (. NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

 El criterio de ordenación no se aplica hasta que el usuario utilice explícitamente uno de los controles de ordenación, cierre y vuelva a abrir el diseñador de variables o bien, cree otra variable.

## <a name="to-create-a-new-variable"></a>Para crear una nueva variable

1.  En Visual Studio, abra una solución de flujo de trabajo o actividad.

2.  En el lienzo de diseño, seleccione una actividad en su flujo de trabajo.

3.  Abra el Diseñador de variables, haga clic en el **Variables** situado en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de variables.

4.  Haga clic en la fila vacía con la etiqueta **crear Variable**. Esto agregará una nueva fila con una nueva variable mediante los siguientes valores predeterminados: variablex para el **nombre** donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de variable únicos,  **Cadena** para el **tipo de Variable**, y **secuencia** para el **ámbito**. No se agrega ningún valor para **predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.

    > [!NOTE]
    > Para eliminar una variable, seleccione la variable haciendo clic en él y, a continuación, presione el **eliminar** clave.

## <a name="see-also"></a>Vea también

- [Usar el Diseñador de flujo de trabajo](developing-applications-with-the-workflow-designer.md)
- [Variables y argumentos](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
- [Cómo: Utilice el Diseñador de argumentos](../workflow-designer/how-to-use-the-argument-designer.md)