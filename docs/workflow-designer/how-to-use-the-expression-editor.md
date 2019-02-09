---
title: 'Diseñador de flujo de trabajo - Cómo: Usar el Editor de expresiones'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fee9738cfce003ef19d311856304d87f6a4b2f15
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "55918915"
---
# <a name="how-to-use-the-expression-editor"></a>Filtrar Usar el Editor de expresiones

El Editor de expresiones es un control del Diseñador de flujo de trabajo que se usa en muchas actividades de flujo de trabajo para escribir y evaluar expresiones. El Editor de expresiones proporciona un IDE completo edición experiencia, incluido IntelliSense, colores, ParamInfo y subrayados ondulados de errores, entre otras características. El compilador valida la expresión después de que se escribe. Si la expresión no es válida, se muestra un icono de error. También se puede abrir el editor como un **Editor de expresiones** cuadro de diálogo.

Las expresiones son valores literales o de código de Visual Basic enlazadas a argumentos o propiedades. Contienen elementos de valor (por ejemplo, variables, constantes, literales, propiedades) que se combinan con operaciones para producir un nuevo valor. Las expresiones se escriben con la sintaxis de VB.NET aunque la aplicación esté en un programa que use C#. Esto significa que la capitalización no importa, la comparación se realiza mediante un único igual inicie sesión ("=" en lugar de "=="), los operadores booleanos son las palabras "y" y "o" en lugar de los símbolos "& &" y "||", y **nada** se usa en lugar de **null**. Para obtener más información sobre las expresiones y operadores en Visual Basic y ver algunos ejemplos, consulte [operadores y expresiones en Visual Basic](/previous-versions/visualstudio/visual-studio-2010/a1w3te48(v=vs.100)).

El **Editor de expresiones** se comporta como sigue:

- Si el foco no está en el Editor de expresiones, tiene la apariencia de un control TextBlock normal.

- Cuando el foco está en el Editor de expresiones, se asemeja y se comporta como el control del Editor de expresiones. Una vez perdido el foco, el Editor de expresiones aspecto nuevo un TextBlock normal.

- Si coloca el foco en el Editor de expresiones en un diseñador de flujo de trabajo hospedado en otro host, se comporta como un TextBox. Cuando el foco se pierde en el diseñador de flujo de trabajo hospedado en otro host, el Editor se asemeja de nuevo a un TextBlock.

> [!NOTE]
> IntelliSense para el Editor de expresiones está disponible solo dentro de Visual Studio. En Visual Studio y los escenarios hospedado en otro host, el compilador valida la expresión después de que se escribe y el editor de expresiones muestra un icono de error si la expresión no es válida.

## <a name="use-the-expression-editor"></a>Usar el Editor de expresiones

1.  En Visual Studio, abra un proyecto de flujo de trabajo nueva o existente.

2.  Por ejemplo, agregue la actividad <xref:System.Activities.Statements.Assign> a su flujo de trabajo.

    > [!NOTE]
    > Hay muchas actividades de flujo de trabajo que tienen editores de expresiones. También aparecen TextBlocks de expresión en el diseñador de variables, diseñador de argumentos y diseñador de argumentos dinámicos. La actividad <xref:System.Activities.Statements.Assign> se utiliza como ejemplo.

3.  Haga clic en el editor de expresiones de la izquierda en el diseñador de actividades para la actividad <xref:System.Activities.Statements.Assign>.

     Las cadenas de marca de agua gris  **\<a >** y  **\<escriba una expresión de VB >** es cadenas de texto de la predeterminada para los editores de expresiones en el <xref:System.Activities.Statements.Assign> actividad.

4.  Escriba su expresión. Si escribe una cadena, asegúrese de colocar comillas dobles en torno a la cadena. Si decide enlazar el argumento de expresión a una variable, no ponga las comillas dobles.

     Cuando haya terminado, seleccione una región o área fuera el Editor de expresiones para desplazar el foco a otra parte del diseñador. Desplazar el foco, hace que el compilador validar la expresión, como se describió anteriormente.

     Una manera alternativa de escribir o editar una expresión es hacer clic en el botón de puntos suspensivos junto al nombre de propiedad en la cuadrícula de propiedades. Al seleccionar el botón de puntos suspensivos se abre el **Editor de expresiones** como un cuadro de diálogo.

## <a name="see-also"></a>Vea también

- <xref:System.Activities.Presentation.View.ExpressionTextBox>