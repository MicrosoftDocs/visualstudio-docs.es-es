---
title: "How to: Create a Nullable Type (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "nullable types, Class Designer"
  - "Class Designer [Visual Studio], nullable types"
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Create a Nullable Type (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ciertos tipos de valor no siempre tienen un valor definido \(o lo necesitan\).  Esto es habitual en las bases de datos, donde algunos campos podrían no tener asignado ningún valor.  Por ejemplo, podría asignar un valor nulo a un campo de base de datos para indicar que todavía no se ha asignado un valor.  
  
 Un *tipo que acepta valores NULL* es un tipo de valor que se extiende para registrar el intervalo normal de valores para ese tipo, además de un valor NULL.  Por ejemplo, a un tipo que acepta valores NULL de `Int32`, que también se denota como Nullable\<Int32\>, se le puede asignar cualquier valor entre \-2147483648 y 2147483647, o el valor NULL.  A un tipo Nullable\<bool\> se le pueden asignar los valores `True`, `False` o NULL \(ningún valor\).  
  
 Los tipos que aceptan valores NULL son instancias de la estructura <xref:System.Nullable%601>.  Cada instancia de un tipo que acepta valores NULL tiene dos propiedades públicas de sólo lectura, `HasValue` y `Value`:  
  
-   `HasValue` es del tipo `bool` e indica si la variable contiene un valor definido.  `True` indica que la variable contiene un valor distinto de NULL.  Puede comprobar un valor definido mediante una instrucción como `if (x.HasValue)` o `if (y != null)`.  
  
-   `Value` es del mismo tipo que el tipo subyacente.  Si `HasValue` es `True`, `Value` contiene un valor significativo.  Si `HasValue` es `False`, al tener acceso a `Value`, se produce una excepción de operación no válida.  
  
 De forma predeterminada, al declarar una variable como un tipo que acepta valores NULL, no tiene ningún valor definido \(`HasValue` es `False`\), excepto el valor predeterminado de su tipo de valor subyacente.  
  
 El Diseñador de clases muestra un tipo que acepta valores NULL de la misma manera que muestra su tipo subyacente.  
  
 Para obtener más información sobre los tipos que aceptan valores NULL en Visual C\#, vea [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index).  Para obtener más información sobre los tipos que aceptan valores NULL en Visual Basic, vea [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Para agregar un tipo que acepta valores NULL mediante el Diseñador de clases  
  
1.  En el diagrama de clases, expanda una clase existente o cree una nueva.  
  
2.  Para agregar una clase al proyecto, en el menú **Diagrama de clases** haga clic en **Agregar** y, a continuación, haga clic en **Agregar clase**.  
  
3.  Para expandir la forma de clase, en el menú **Diagrama de clases**, haga clic en **Expandir**.  
  
4.  Seleccione la forma de clase.  En el menú **Diagrama de clases**, haga clic en **Agregar** y, a continuación, haga clic en **Campo**.  Aparece un nuevo campo con el nombre predeterminado **Campo** en la forma de clase y también en la ventana **Detalles de clase**.  
  
5.  En la columna **Nombre** de la ventana **Detalles de clase** \(o en la propia forma de clase\), cambie el nombre del nuevo campo por un nombre válido y más significativo.  
  
6.  En la columna **Tipo** de la ventana **Detalles de clase**, declare el tipo como un tipo que acepta valores NULL, como se muestra en el código siguiente:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
### Para agregar un tipo que acepta valores NULL mediante el Editor de código  
  
1.  Agregue una clase al proyecto.  Seleccione el nodo de proyecto en el **Explorador de soluciones** y, en el menú **Proyecto**, haga clic en **Agregar clase**.  
  
2.  En el archivo .cs o .vb para la nueva clase, agregue uno o más tipos que acepten valores NULL en la nueva clase a la declaración de clase.  
  
3.  En la vista de clases, arrastre el nuevo icono de clase a la superficie de diseño del Diseñador de clases.  Una forma de clase aparece en el diagrama de clases.  
  
4.  Expanda los detalles de la forma de clase y mueva el puntero del mouse sobre los miembros de clase.  La información sobre herramientas muestra la declaración de cada miembro.  
  
5.  Haga clic con el botón secundario en la forma de clase y haga clic en **Detalles de clase**.  Puede ver o modificar las propiedades del nuevo tipo en la ventana **Detalles de clase**.  
  
## Vea también  
 <xref:System.Nullable%601>   
 [Tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/index)   
 [Utilizar tipos que aceptan valores NULL](/dotnet/csharp/programming-guide/nullable-types/using-nullable-types)   
 [Cómo: Identificar tipos que aceptan valores NULL](../Topic/How%20to:%20Identify%20a%20Nullable%20Type%20\(C%23%20Programming%20Guide\).md)   
 [Tipos de valor que aceptan valores NULL](/dotnet/visual-basic/programming-guide/language-features/data-types/nullable-value-types)