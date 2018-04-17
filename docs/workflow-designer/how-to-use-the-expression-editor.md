---
title: 'Cómo: usar el Editor de expresiones | Documentos de Microsoft'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ExpressionTextBox.UI
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f9873d341238f3278779277d70da6df56f29f721
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-the-expression-editor"></a>Cómo: Utilizar el Editor de expresiones
El Editor de expresiones es un control del Diseñador de flujo de trabajo de Windows que se utiliza en muchas actividades de flujo de trabajo como un medio para especificar y evaluar estas expresiones. El Editor de expresiones proporciona una experiencia de edición IDE completa, que incluye IntelliSense, el uso de distintos colores, ParamInfo y subrayados ondulados de errores, entre otras características. El compilador valida la expresión una vez se ha escrito. Si la expresión no es válida, se muestra un icono de error. También se puede abrir el editor como un **Editor de expresiones** cuadro de diálogo.

 Las expresiones son valores literales o de código de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] enlazadas a argumentos o propiedades. Contienen elementos de valor (p. ej. variables, constantes, literales, propiedades) que se combinan con operaciones para proporcionar un nuevo valor. Las expresiones se escriben con la sintaxis de VB.NET aunque la aplicación esté en un programa que use C#. Esto significa mayúsculas y minúsculas no es relevante, la comparación se realiza utilizando un único es igual a inicio de sesión ("=") en lugar de ("=="), los operadores booleanos son las palabras "y" y "o" en lugar de los símbolos "& &" y "&#124;&#124;", y **nada**  se utiliza en lugar de **null**. Para obtener más información sobre las expresiones y operadores en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y algunos ejemplos, vea [operadores y expresiones en Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).

 El **Editor de expresiones** se comporta como sigue:

-   Si el foco no está en el Editor de expresiones, tiene la apariencia de un control TextBlock normal.

-   Cuando el foco está en el Editor de expresiones, se asemeja y se comporta como el control del Editor de expresiones. Tras haber perdido el foco, se vuelve a parecer a un TextBlock normal.

-   Si coloca el foco en el Editor de expresiones en un diseñador de flujo de trabajo hospedado en otro host, se comporta como un TextBox. Cuando el foco se pierde en el diseñador de flujo de trabajo hospedado en otro host, el Editor se asemeja de nuevo a un TextBlock.

> [!NOTE]
> IntelliSense para el Editor de expresiones solo está disponible en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]. Tanto en [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], como en escenarios hospedados en otro host, el compilador valida la expresión una vez se ha especificado y el Editor de expresiones muestra un icono de error si la expresión no es válida.

### <a name="using-the-expression-editor"></a>Utilizar el Editor de expresiones

1.  En [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)], abra un proyecto de flujo de trabajo nuevo o uno existente.

2.  Por ejemplo, agregue la actividad <xref:System.Activities.Statements.Assign> a su flujo de trabajo.

    > [!NOTE]
    > Hay muchas actividades de flujo de trabajo que tienen editores de expresiones. También aparecen TextBlocks de expresión en el diseñador de variables, diseñador de argumentos y diseñador de argumentos dinámicos. La actividad <xref:System.Activities.Statements.Assign> se utiliza como ejemplo.

3.  Haga clic en el editor de expresiones de la izquierda en el diseñador de actividades para la actividad <xref:System.Activities.Statements.Assign>.

     Las cadenas de marca de agua gris  **\<a >** y  **\<escriba una expresión de VB >** es cadenas de texto de manera predeterminada para los editores de expresiones en la <xref:System.Activities.Statements.Assign> actividad.

4.  Escriba su expresión. Si escribe una cadena, asegúrese de colocar comillas dobles en torno a la cadena. Si decide enlazar el argumento de expresión a una variable, no ponga las comillas dobles.

     Cuando haya terminado, seleccione una región o área fuera del Editor de expresiones para desplazar el foco hacia otra parte del diseñador. Esto hará que el compilador valide la expresión tal como se describe previamente.

     Una forma alternativa de escribir o modificar una expresión es hacer clic en los puntos suspensivos junto al nombre de la propiedad en la cuadrícula de propiedades. Se abrirá la **Editor de expresiones** como cuadro de diálogo.

## <a name="see-also"></a>Vea también

- <xref:System.Activities.Presentation.View.ExpressionTextBox>