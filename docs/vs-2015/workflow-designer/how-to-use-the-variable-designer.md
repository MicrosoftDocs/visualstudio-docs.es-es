---
title: 'Cómo: usar el diseñador de variables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.DesignTimeVariable.UI
ms.assetid: 0318dfb0-bf8f-4f92-9b86-ae4c1b2161ad
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4744864824da5efb238e9af1a5a12fcef79ea4ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659075"
---
# <a name="how-to-use-the-variable-designer"></a>Utilizar el diseñador de variables
El diseñador variables se utiliza para crear variables con el fin de utilizarlas en escenarios de enlace de datos e instrucciones condicionales. Se tiene acceso al diseñador haciendo clic en el botón **variables** en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de variables que aparecen en un formulario tabular y se pueden ordenar por cada uno de los encabezados de columna, excepto por la columna **predeterminada** . Cada variable contiene un nombre, tipo de variable, ámbito y valor predeterminado (en su caso). El nombre y valor predeterminado son campos de texto editable, y el tipo y ámbito son listas desplegables. El ámbito es la actividad que se seleccionó cuando se invocó el diseñador de variables. Si no se puede crear una variable en el ámbito de la selección, el ámbito tendrá como valor predeterminado la actividad antecesora más próxima de la selección que permita la creación de variables en su ámbito. [!INCLUDE[crabout](../includes/crabout-md.md)] variables, vea [variables y argumentos](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

 El criterio de ordenación no se aplica hasta que el usuario utilice explícitamente uno de los controles de ordenación, cierre y vuelva a abrir el diseñador de variables o bien, cree otra variable.

### <a name="to-create-a-new-variable"></a>Para crear una nueva variable

1. Abra un flujo de trabajo o solución de actividades en [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

2. En el lienzo de diseño, seleccione una actividad en su flujo de trabajo.

3. Abra el diseñador de variables haciendo clic en el botón **variables** en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de variables.

4. Haga clic en la fila vacía con la etiqueta **crear variable**. Esto agregará una nueva fila con una nueva variable con los siguientes valores predeterminados: variablex para el **nombre** , donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de variable únicos, una **cadena** para el **tipo de variable**y una **secuencia** para el **ámbito**. No se agrega ningún valor para el valor **predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.

    > [!NOTE]
    > Para eliminar una variable, seleccione la variable haciendo clic en ella y, a continuación, presione la tecla **Supr** .

## <a name="see-also"></a>Consulte también
 Usar [el diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md) [variables y argumentos](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) [Cómo: usar el diseñador de argumentos](../workflow-designer/how-to-use-the-argument-designer.md)