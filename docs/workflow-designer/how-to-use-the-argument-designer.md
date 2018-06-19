---
title: 'Diseñador de flujo de trabajo: Cómo: utilizar el Diseñador de argumentos'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b94656c7242c4bc6bc1dd1430230dac62a5322f1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
ms.locfileid: "31971877"
---
# <a name="how-to-use-the-argument-designer"></a>Utilizar el diseñador de argumentos

En comparación con versiones anteriores de .NET Framework, el Diseñador de argumentos facilita al permitir que los datos fluyen hacia dentro y fuera de una actividad. El diseñador se tiene acceso haciendo clic en el **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de argumentos que aparecen en un formato tabular y pueden ordenarse por cada uno de los encabezados de columna, excepto para la **valor predeterminado** columna. Cada argumento contiene un nombre, dirección IN/OUT/IN-OUT/PROPERTY, tipo y valor de la expresión predeterminado (en su caso). El nombre y el valor de la expresión predeterminado son campos de texto editable y el tipo y la dirección son listas desplegables. Para obtener más información, consulte [Variables y argumentos (. NET)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Para crear un argumento nuevo

1.  Abra una solución de flujo de trabajo o actividad en Visual Studio 2010.

2.  Abra el Diseñador de argumentos, haga clic en el **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de argumentos.

3.  Haga clic en la fila vacía con la etiqueta **crear argumento**. Esto agregará una nueva fila con un nuevo argumento mediante los siguientes valores predeterminados: argumentx para el **nombre** donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de argumento único, **en**  para el **dirección**, y **cadena** para el **tipo de argumento**. No se agrega ningún valor para **valor predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.

    > [!NOTE]
    > Para eliminar un argumento, seleccione el argumento haciendo clic en él y, a continuación, presione la **eliminar** clave.

## <a name="see-also"></a>Vea también

- [Usar el Diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md)
- [Variables y argumentos](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)