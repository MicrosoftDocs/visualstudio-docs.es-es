---
title: 'Diseñador de flujo de trabajo: Cómo usar el editor de expresiones'
description: Obtenga información sobre cómo el editor de expresiones es un control de Diseñador de flujo de trabajo que puede usar en muchas actividades de flujo de trabajo para especificar y evaluar expresiones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 855326085a51ec6590bd1b3f0e1e5565c53396cb
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437858"
---
# <a name="how-to-use-the-expression-editor"></a>Cómo: Utilizar el Editor de expresiones

El editor de expresiones es un control de Diseñador de flujo de trabajo que se usa en muchas actividades de flujo de trabajo para especificar y evaluar expresiones. El editor de expresiones proporciona una experiencia de edición de IDE completa, como IntelliSense, coloración, ParamInfo, subrayados ondulados de errores, entre otras características. El compilador valida la expresión una vez que se ha escrito. Si la expresión no es válida, se muestra un icono de error. El editor también puede abrirse como un cuadro de diálogo del **Editor de expresiones** .

Las expresiones son valores literales o de código de Visual Basic enlazadas a argumentos o propiedades. Contienen elementos de valor (por ejemplo, variables, constantes, literales, propiedades) que se combinan con operaciones para producir un nuevo valor. Las expresiones se escriben con la sintaxis de VB.NET aunque la aplicación esté en un programa que use C#. Esto significa que el uso de mayúsculas no importa, la comparación se realiza mediante un único signo igual ("=" en lugar de "= ="), los operadores booleanos son las palabras "and" y "or" en lugar de los símbolos "&&" y "| |", y no se utiliza **nada** en lugar de **null**. Para obtener más información sobre las expresiones y los operadores de Visual Basic y para algunos ejemplos, vea [operadores y expresiones en Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

El **Editor de expresiones** se comporta de la siguiente manera:

- Si el foco no está en el Editor de expresiones, tiene la apariencia de un control TextBlock normal.

- Cuando el foco está en el Editor de expresiones, se asemeja y se comporta como el control del Editor de expresiones. Una vez que pierde el foco, el editor de expresiones vuelve a tener el aspecto de un TextBlock normal.

- Si coloca el foco en el Editor de expresiones en un diseñador de flujo de trabajo hospedado en otro host, se comporta como un TextBox. Cuando el foco se pierde en el diseñador de flujo de trabajo hospedado en otro host, el Editor se asemeja de nuevo a un TextBlock.

> [!NOTE]
> IntelliSense para el editor de expresiones solo está disponible dentro de Visual Studio. En los escenarios de Visual Studio y rehospedado, el compilador valida la expresión una vez que se ha escrito y el editor de expresiones muestra un icono de error si la expresión no es válida.

## <a name="use-the-expression-editor"></a>Usar el Editor de expresiones

1. En Visual Studio, abra un proyecto de flujo de trabajo nuevo o existente.

2. Por ejemplo, agregue la actividad <xref:System.Activities.Statements.Assign> a su flujo de trabajo.

    > [!NOTE]
    > Hay muchas actividades de flujo de trabajo que tienen editores de expresiones. También aparecen TextBlocks de expresión en el diseñador de variables, diseñador de argumentos y diseñador de argumentos dinámicos. La actividad <xref:System.Activities.Statements.Assign> se utiliza como ejemplo.

3. Haga clic en el editor de expresiones de la izquierda en el diseñador de actividades para la actividad <xref:System.Activities.Statements.Assign>.

     Las cadenas de marca de agua gris **\<To>** y **\<Enter a VB Expression>** son las cadenas de texto predeterminadas para los editores de expresiones en la <xref:System.Activities.Statements.Assign> actividad.

4. Escriba su expresión. Si escribe una cadena, asegúrese de colocar comillas dobles en torno a la cadena. Si decide enlazar el argumento de expresión a una variable, no ponga las comillas dobles.

     Cuando haya terminado, seleccione una región o área fuera del editor de expresiones para desplazar el foco a otra parte del diseñador. Al cambiar el foco, el compilador valida la expresión tal y como se ha descrito anteriormente.

     Una manera alternativa de escribir o editar una expresión es hacer clic en los puntos suspensivos junto al nombre de la propiedad en la cuadrícula de propiedades. Al seleccionar los puntos suspensivos se abre el **Editor de expresiones** como un cuadro de diálogo.

## <a name="see-also"></a>Consulte también

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
