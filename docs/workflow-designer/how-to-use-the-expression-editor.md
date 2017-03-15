---
title: "C&#243;mo: Utilizar el Editor de expresiones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Presentation.View.ExpressionTextBox.UI"
ms.assetid: b5f961dd-6dda-41a9-9cae-0383d479ef3d
caps.latest.revision: 13
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# C&#243;mo: Utilizar el Editor de expresiones
El Editor de expresiones es un control de [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] que se utiliza en muchas actividades de flujo de trabajo como un medio para especificar y evaluar estas expresiones.  El Editor de expresiones proporciona una experiencia de edición IDE completa, que incluye IntelliSense, el uso de distintos colores, ParamInfo y subrayados ondulados de errores, entre otras características.  El compilador valida la expresión una vez se ha escrito.  Si la expresión no es válida, se muestra un icono de error.  El editor también se puede abrir como cuadro de diálogo **Editor de expresiones**.  
  
 Las expresiones son valores literales o de código de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] enlazadas a argumentos o propiedades.  Contienen elementos de valor \(por ejemplo,  variables, constantes, literales, propiedades\) que se combinan con operaciones para producir un nuevo valor.  Las expresiones se escriben con la sintaxis de VB.NET aunque la aplicación esté en un programa que use C\#.  Esto significa que el uso de mayúsculas no es relevante, que la comparación se realiza utilizando un signo igual simple \("\="\) en lugar de \(" \=\="\), que los operadores booleanos son las palabras "y" y "o" en lugar de los símbolos "&&" y "&#124;&#124;" y que **Nothing** se utiliza en lugar de **null**.  Para obtener más información acerca de las expresiones y los operadores en [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] y ver algunos ejemplos, consulte [Operadores y expresiones en Visual Basic](http://go.microsoft.com/fwlink/?LinkId=186818).  
  
 El **Editor de expresiones** se comporta de la siguiente forma:  
  
-   Si el foco no está en el Editor de expresiones, tiene la apariencia de un control TextBlock normal.  
  
-   Cuando el foco está en el Editor de expresiones, se asemeja y se comporta como el control del Editor de expresiones.  Tras haber perdido el foco, se vuelve a parecer a un TextBlock normal.  
  
-   Si coloca el foco en el Editor de expresiones en un diseñador de flujo de trabajo hospedado en otro host, se comporta como un TextBox.  Cuando el foco se pierde en el diseñador de flujo de trabajo hospedado en otro host, el Editor se asemeja de nuevo a un TextBlock.  
  
> [!NOTE]
>  IntelliSense para el Editor de expresiones solo está disponible en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  Tanto en [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], como en escenarios hospedados en otro host, el compilador valida la expresión una vez se ha especificado y el Editor de expresiones muestra un icono de error si la expresión no es válida.  
  
### Utilizar el Editor de expresiones  
  
1.  En [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], abra un proyecto de flujo de trabajo nuevo o uno existente.  
  
2.  Por ejemplo, agregue la actividad <xref:System.Activities.Statements.Assign> a su flujo de trabajo.  
  
    > [!NOTE]
    >  Hay muchas actividades de flujo de trabajo que tienen editores de expresiones.  También aparecen TextBlocks de expresión en el diseñador de variables, diseñador de argumentos y diseñador de argumentos dinámicos.  La actividad <xref:System.Activities.Statements.Assign> se utiliza como ejemplo.  
  
3.  Haga clic en el editor de expresiones de la izquierda en el diseñador de actividades para la actividad <xref:System.Activities.Statements.Assign>.  
  
     Las cadenas de la marca de agua gris **\<Para\>** y **\<Escriba una expresión de VB\>** son las cadenas de texto predeterminado para los editores de expresión en la actividad <xref:System.Activities.Statements.Assign>.  
  
4.  Escriba su expresión.  Si escribe una cadena, asegúrese de colocar comillas dobles en torno a la cadena.  Si decide enlazar el argumento de expresión a una variable, no ponga las comillas dobles.  
  
     Cuando haya terminado, seleccione una región o área fuera del Editor de expresiones para desplazar el foco hacia otra parte del diseñador.  Esto hará que el compilador valide la expresión tal como se describe previamente.  
  
     Una forma alternativa de escribir o modificar una expresión es hacer clic en los puntos suspensivos junto al nombre de la propiedad en la cuadrícula de propiedades.  Esto abrirá el **Editor de expresiones** como un cuadro de diálogo.  
  
## Vea también  
 <xref:System.Activities.Presentation.View.ExpressionTextBox>