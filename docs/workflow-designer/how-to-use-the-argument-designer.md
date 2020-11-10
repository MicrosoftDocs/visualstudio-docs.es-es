---
title: 'Diseñador de flujo de trabajo: Cómo usar el diseñador de argumentos'
description: Obtenga información sobre el diseñador de argumentos y cómo usar el diseñador de argumentos para permitir que los datos fluyan dentro y fuera de una actividad.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aca39eaf94e5dca3159a9f3740dae0f87257d9c1
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437871"
---
# <a name="how-to-use-the-argument-designer"></a>Utilizar el diseñador de argumentos

El diseñador de argumentos facilita permitir que los datos fluyan dentro y fuera de una actividad. Para acceder al diseñador, haga clic en el botón **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. El diseñador contiene una lista de argumentos que aparecen en un formulario tabular y que se pueden ordenar por cada uno de los encabezados de columna, excepto por la columna **valor predeterminado** . Cada argumento contiene un nombre, dirección IN/OUT/IN-OUT/PROPERTY, tipo y valor de la expresión predeterminado (en su caso). El nombre y el valor de la expresión predeterminado son campos de texto editable y el tipo y la dirección son listas desplegables. Para obtener más información, vea [variables y argumentos (.net)](/dotnet/framework/windows-workflow-foundation/variables-and-arguments).

## <a name="to-create-a-new-argument"></a>Para crear un argumento nuevo

1. Abra una solución de flujo de trabajo o actividad en Visual Studio.

2. Abra el diseñador de argumentos haciendo clic en el botón **argumentos** situado en la esquina inferior izquierda del lienzo de diseño. Aparecerá el diseñador de argumentos.

3. Haga clic en la fila vacía con la etiqueta **crear argumento**. Esto agregará una nueva fila con un nuevo argumento usando los siguientes valores predeterminados: argumentx para el **nombre** , donde x es un entero con un valor inicial de 1 que se incrementa automáticamente para crear nombres de argumentos únicos, **en** para la **Dirección** y la **cadena** para el **tipo de argumento**. No se agrega ningún valor para el **valor predeterminado**. Podrá cambiar estos valores en cualquier momento durante el proceso de diseño del flujo de trabajo.

    > [!NOTE]
    > Para eliminar un argumento, seleccione el argumento haciendo clic en él y, a continuación, presione la tecla **Supr** .

## <a name="see-also"></a>Consulte también

- [Usar el Diseñador de flujo de trabajo](developing-applications-with-the-workflow-designer.md)
- [Variables y argumentos](/dotnet/framework/windows-workflow-foundation/variables-and-arguments)
