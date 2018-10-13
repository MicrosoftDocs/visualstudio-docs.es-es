---
title: 'Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b8fd24f6c1e9b0427746296efa9a839bf46ed7ca
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220095"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al modificar o agregar las plantillas de texto en una solución de lenguaje específico de dominio, es posible que obtenga errores cuando el motor transforma la plantilla al código fuente, o bien cuando se compila el código generado. El siguiente tutorial muestra algunas de las cosas que puede hacer para depurar una plantilla de texto.  
  
> [!NOTE]
>  Para obtener más información sobre el texto de las plantillas en general, vea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md). Para obtener más información sobre la depuración de plantillas de texto, consulte [Tutorial: depurar una plantilla de texto](http://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Creación de una solución de lenguaje específico de dominio  
 En este procedimiento, creará una solución de lenguaje específico de dominio que tiene las siguientes características:  
  
-   Nombre: DebuggingTestLanguage  
  
-   Plantilla de solución: lenguaje mínimo  
  
-   Extensión de archivo: .ddd  
  
-   Nombre de la compañía: Fabrikam  
  
 Para obtener más información acerca de cómo crear una solución de lenguaje específico de dominio, consulte [Cómo: crear soluciones de lenguajes específicos de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Creación de una plantilla de texto  
 Agregar una plantilla de texto a la solución.  
  
#### <a name="to-create-a-text-template"></a>Para crear una plantilla de texto  
  
1.  Compile la solución y comenzar a ejecutarla en el depurador. (En el **compilar** menú, haga clic en **recompilar solución**y, a continuación, en el **depurar** menú, haga clic en **Iniciar depuración**.) Una nueva instancia de Visual Studio abre el proyecto de depuración.  
  
2.  Agregue un archivo de texto denominado `DebugTest.tt` para el proyecto de depuración.  
  
3.  Asegúrese de que el **Custom Tool** propiedad de DebugTest.tt está establecida en `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Depuración de las directivas que tienen acceso a un modelo desde una plantilla de texto  
 Antes de que puede tener acceso a un modelo de las instrucciones y expresiones en una plantilla de texto, primero debe llamar a un procesador de directivas personalizadas. Llamar el procesador de directivas personalizadas hace que las clases en el modelo disponible para el código de plantilla de texto como propiedades. Para obtener más información, consulte [acceso a los modelos de plantillas de texto](../modeling/accessing-models-from-text-templates.md).  
  
 En los procedimientos siguientes, que desea depurar un nombre de la directiva incorrecto y un nombre de propiedad incorrecto.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Para depurar un nombre de directiva incorrecto  
  
1.  Reemplace el código de DebugTest.tt con el código siguiente:  
  
    > [!NOTE]
    >  El código contiene un error. Que va a presentar el error con el fin de depurarla.  
  
    ```csharp  
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
  
    ```vb  
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
  
     **El procesador denominado 'DebuggingTestLanguageDirectiveProcessor' no es compatible con la directiva denominada 'modelRoot'. La transformación no se ejecutará.**  
  
     En este caso, la llamada de directiva contiene un nombre de directiva incorrecto. Ha especificado `modelRoot` como el nombre de la directiva, pero el nombre de la directiva correcto es `DebuggingTestLanguage`.  
  
3.  Haga doble clic en el error en la **lista de errores** ventana para saltar al código.  
  
4.  Para corregir el código, cambie el nombre de la directiva a `DebuggingTestLanguage`.  
  
     Se resalta el cambio.  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  En **el Explorador de soluciones**, haga clic en DebugTest.tt y, a continuación, haga clic en **ejecutar herramienta personalizada**.  
  
     Ahora el sistema transforma la plantilla de texto y genera el archivo de salida correspondiente. No verá los errores en el **lista de errores** ventana.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Para depurar un nombre de propiedad incorrecto  
  
1.  Reemplace el código de DebugTest.tt con el código siguiente:  
  
    > [!NOTE]
    >  El código contiene un error. Que va a presentar el error con el fin de depurarla.  
  
    ```csharp  
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
  
    ```vb  
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
  
     En este caso, el código de plantilla de texto contiene un nombre de propiedad incorrecto. Ha especificado `ExampleModel` como el nombre de propiedad, pero la propiedad correcta nombre es `LibraryModel`. Puede encontrar el nombre de la propiedad correcta en la proporciona el parámetro, tal como se muestra en el código siguiente:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Haga doble clic en el error en la ventana Lista de errores para saltar al código.  
  
4.  Para corregir el código, cambie el nombre de propiedad a `LibraryModel` en el código de plantilla de texto.  
  
     Los cambios aparecen resaltados.  
  
    ```csharp  
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
  
    ```vb  
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



