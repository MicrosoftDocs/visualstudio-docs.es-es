---
title: 'Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7bbe2b592dc315bc0885e1f1ca4c890e4e66255d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo
Al modificar o agregar plantillas de texto en una solución de lenguaje específico de dominio, puede obtener errores cuando el motor transforma la plantilla de código fuente o cuando se compila el código generado. El tutorial siguiente muestra algunas de las cosas que puede hacer para depurar una plantilla de texto.  
  
> [!NOTE]
>  Para obtener más información sobre el texto de las plantillas en general, vea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md). Para obtener más información acerca de la depuración de plantillas de texto, consulte [Tutorial: depurar una plantilla de texto](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Creación de una solución de lenguaje específico de dominio  
 En este procedimiento, se crea una solución de lenguaje específico de dominio que tiene las siguientes características:  
  
-   Nombre: DebuggingTestLanguage  
  
-   Plantilla de solución: lenguaje mínima  
  
-   Extensión de archivo: .ddd  
  
-   Nombre de la compañía: Fabrikam  
  
 Para obtener más información acerca de cómo crear una solución de lenguaje específico de dominio, consulte [Cómo: crear una solución de lenguaje específico de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Crear una plantilla de texto  
 Agregar una plantilla de texto a la solución.  
  
#### <a name="to-create-a-text-template"></a>Para crear una plantilla de texto  
  
1.  Compile la solución y comenzar a ejecutarse en el depurador. (En el **crear** menú, haga clic en **volver a generar solución**y, a continuación, en la **depurar** menú, haga clic en **Iniciar depuración**.) Una nueva instancia de Visual Studio abre el proyecto de depuración.  
  
2.  Agregue un archivo de texto denominado `DebugTest.tt` al proyecto de depuración.  
  
3.  Asegúrese de que el **herramienta personalizada** propiedad de DebugTest.tt se establece en `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Depuración de directivas que tienen acceso a un modelo de una plantilla de texto  
 Antes de que puede tener acceso a un modelo de las instrucciones y expresiones en una plantilla de texto, debe llamar primero a un procesador de directivas personalizadas. Llamar el procesador de directivas generado hace que las clases del modelo disponible para el código de plantilla de texto como propiedades. Para obtener más información, consulte [acceso a modelos de plantillas de texto](../modeling/accessing-models-from-text-templates.md).  
  
 En los procedimientos siguientes, que desea depurar un nombre de directiva incorrecto y un nombre de propiedad incorrecto.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Para depurar un nombre de directiva incorrecto  
  
1.  Reemplace el código de DebugTest.tt por el siguiente código:  
  
    > [!NOTE]
    >  El código contiene un error. Agregamos el error para depurarlo.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  En **el Explorador de soluciones**, haga clic en DebugTest.tt y, a continuación, haga clic en **ejecutar herramienta personalizada**.  
  
     El **lista de errores** ventana muestra este error:  
  
     **El procesador denominado 'DebuggingTestLanguageDirectiveProcessor' no admite la directiva denominada 'modelRoot'. La transformación no se ejecutará.**  
  
     En este caso, la llamada de directiva contiene un nombre de directiva incorrecto. Ha especificado `modelRoot` como el nombre de la directiva, pero el nombre correcto de la directiva es `DebuggingTestLanguage`.  
  
3.  Haga doble clic en el error en la **lista de errores** ventana para saltar al código.  
  
4.  Para corregir el código, cambie el nombre de la directiva a `DebuggingTestLanguage`.  
  
     Se resalta el cambio.  
  
    ```c#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  En **el Explorador de soluciones**, haga clic en DebugTest.tt y, a continuación, haga clic en **ejecutar herramienta personalizada**.  
  
     Ahora el sistema transforma la plantilla de texto y genera el archivo de salida correspondiente. No verá los errores en el **lista de errores** ventana.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Para depurar un nombre de propiedad incorrecto  
  
1.  Reemplace el código de DebugTest.tt por el siguiente código:  
  
    > [!NOTE]
    >  El código contiene un error. Agregamos el error para depurarlo.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  En el **el Explorador de soluciones**, haga clic en DebugTest.tt y, a continuación, haga clic en **ejecutar herramienta personalizada**.  
  
     El **lista de errores** ventana aparece y muestra uno de estos errores:  
  
     (C#)  
  
     **Compilando transformación: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' no contiene una definición para 'ExampleModel'**  
  
     (Visual Basic)  
  
     **Compilando transformación: 'ExampleModel' no es un miembro de ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     En este caso, el código de plantilla de texto contiene un nombre de propiedad incorrecto. Ha especificado `ExampleModel` como el nombre de propiedad, pero la propiedad correcta nombre es `LibraryModel`. Puede encontrar el nombre de la propiedad correcta en la proporciona el parámetro, como se muestra en el código siguiente:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Haga doble clic en el error en la ventana Lista de errores para saltar al código.  
  
4.  Para corregir el código, cambie el nombre de propiedad a `LibraryModel` en el código de plantilla de texto.  
  
     Se resaltan los cambios.  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  En **el Explorador de soluciones**, haga clic en DebugTest.tt y, a continuación, haga clic en **ejecutar herramienta personalizada**.  
  
     Ahora el sistema transforma la plantilla de texto y genera el archivo de salida correspondiente. No verá los errores en el **lista de errores** ventana.
