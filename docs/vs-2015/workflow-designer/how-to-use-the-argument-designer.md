---
title: 'Cómo: usar el diseñador de argumentos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659114"
---
# <a name="how-to-use-the-argument-designer"></a>Utilizar el diseñador de argumentos
Si se compara con las versiones anteriores de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], el diseñador de argumentos hace más fácil permitir el flujo de datos dentro y fuera de una actividad. Se tiene acceso al diseñador haciendo clic en el botón **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de argumentos que aparecen en un formulario tabular y que se pueden ordenar por cada uno de los encabezados de columna, excepto por la columna **valor predeterminado** . Cada argumento contiene un nombre, dirección IN/OUT/IN-OUT/PROPERTY, tipo y valor de la expresión predeterminado (en su caso). El nombre y el valor de la expresión predeterminado son campos de texto editable y el tipo y la dirección son listas desplegables. [!INCLUDE[crabout](../includes/crabout-md.md)] los argumentos, vea [variables y argumentos](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Para crear un argumento nuevo

1. Abra un flujo de trabajo o solución de actividades en [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. Abra el diseñador de argumentos haciendo clic en el botón **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de argumentos.

3. Haga clic en la fila vacía con la etiqueta **crear argumento**. Esto agregará una nueva fila con un nuevo argumento usando los siguientes valores predeterminados: argumentx para el **nombre** , donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de argumentos únicos, **en** para la **Dirección**y la **cadena** para el **tipo de argumento**. No se agrega ningún valor para el **valor predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.

    > [!NOTE]
    > Para eliminar un argumento, seleccione el argumento haciendo clic en él y, a continuación, presione la tecla **Supr** .

## <a name="see-also"></a>Consulte también
 [Usar el diseñador de flujo de trabajo](../workflow-designer/using-the-workflow-designer.md) [variables y argumentos](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8)