---
title: 'Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo'
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f592cfbd46e0f4fc3a64ecaabadf17a6754480c0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593530"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo
Al modificar o agregar plantillas de texto en una solución de lenguaje específico de dominio, es posible que se produzcan errores cuando el motor transforme la plantilla en código fuente o cuando compile el código generado. En el siguiente tutorial se muestran algunas de las cosas que puede hacer para depurar una plantilla de texto.

> [!NOTE]
> Para obtener más información sobre las plantillas de texto en general, vea [generación de código y plantillas de texto T4](../modeling/code-generation-and-t4-text-templates.md). Para obtener más información sobre la depuración de plantillas de texto, vea [Tutorial: depurar una plantilla de texto](debugging-a-t4-text-template.md).

## <a name="creating-a-domain-specific-language-solution"></a>Crear una solución de lenguaje específico de dominio
 En este procedimiento, creará una solución de lenguaje específico de dominio que tiene las siguientes características:

- Nombre: DebuggingTestLanguage

- Plantilla de solución: idioma mínimo

- Extensión de archivo:. DDD

- Nombre de la compañía: fabrikam

  Para obtener más información sobre cómo crear una solución de lenguaje específico de dominio, consulte [Cómo: crear una solución de lenguaje específico de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Crear una plantilla de texto
 Agregue una plantilla de texto a la solución.

#### <a name="to-create-a-text-template"></a>Para crear una plantilla de texto

1. Compile la solución y comience a ejecutarla en el depurador. (En el menú **compilar** , haga clic en **recompilar solución**y, a continuación, en el menú **depurar** , haga clic en **iniciar depuración**). Una nueva instancia de Visual Studio abre el proyecto de depuración.

2. Agregue un archivo de texto denominado `DebugTest.tt` al proyecto de depuración.

3. Asegúrese de que la propiedad **herramienta personalizada** de DebugTest.TT está establecida en `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Directivas de depuración que obtienen acceso a un modelo desde una plantilla de texto
 Para poder tener acceso a un modelo desde las instrucciones y expresiones de una plantilla de texto, primero debe llamar a un procesador de directivas generado. La llamada al procesador de directivas generado hace que las clases del modelo estén disponibles para el código de plantilla de texto como propiedades. Para obtener más información, consulte [acceso a los modelos de plantillas de texto](../modeling/accessing-models-from-text-templates.md).

 En los siguientes procedimientos, depurará un nombre de directiva incorrecto y un nombre de propiedad incorrecto.

#### <a name="to-debug-an-incorrect-directive-name"></a>Para depurar un nombre de directiva incorrecto

1. Reemplace el código de DebugTest.tt por el código siguiente:

    > [!NOTE]
    > El código contiene un error. Está introduciendo el error para depurarlo.

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

2. En **Explorador de soluciones**, haga clic con el botón secundario en DebugTest.TT y, a continuación, haga clic en **Ejecutar herramienta personalizada**.

     La ventana **lista de errores** muestra este error:

     **El procesador denominado ' DebuggingTestLanguageDirectiveProcessor ' no admite la Directiva denominada ' modelRoot '. La transformación no se ejecutará.**

     En este caso, la llamada a la Directiva contiene un nombre de directiva incorrecto. Ha especificado `modelRoot` como nombre de la Directiva, pero el nombre de la Directiva correcta es `DebuggingTestLanguage`.

3. Haga doble clic en el error en la ventana **lista de errores** para saltar al código.

4. Para corregir el código, cambie el nombre de la Directiva a `DebuggingTestLanguage`.

     Se resalta el cambio.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. En **Explorador de soluciones**, haga clic con el botón secundario en DebugTest.TT y, a continuación, haga clic en **Ejecutar herramienta personalizada**.

     Ahora el sistema transforma la plantilla de texto y genera el archivo de salida correspondiente. No verá ningún error en la ventana **lista de errores** .

#### <a name="to-debug-an-incorrect-property-name"></a>Para depurar un nombre de propiedad incorrecto

1. Reemplace el código de DebugTest.tt por el código siguiente:

    > [!NOTE]
    > El código contiene un error. Está introduciendo el error para depurarlo.

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

2. En **Explorador de soluciones**, haga clic con el botón secundario en DebugTest.TT y, a continuación, haga clic en **Ejecutar herramienta personalizada**.

     Aparece la ventana **lista de errores** y muestra uno de estos errores:

     (C#)

     **Compilando transformación: Microsoft. VisualStudio. TextTemplating\<GUID >. GeneratedTextTransformation ' no contiene una definición para ' ExampleModel '**

     (Visual Basic)

     **Compilando transformación: ' ExampleModel ' no es un miembro de ' Microsoft. VisualStudio. TextTemplating\<GUID >. GeneratedTextTransformation'.**

     En este caso, el código de la plantilla de texto contiene un nombre de propiedad incorrecto. Ha especificado `ExampleModel` como el nombre de la propiedad, pero el nombre de propiedad correcto es `LibraryModel`. Puede encontrar el nombre de propiedad correcto en el parámetro proporciona, tal y como se muestra en el código siguiente:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Haga doble clic en el error en la ventana Lista de errores para saltar al código.

4. Para corregir el código, cambie el nombre de la propiedad a `LibraryModel` en el código de la plantilla de texto.

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

5. En **Explorador de soluciones**, haga clic con el botón secundario en DebugTest.TT y, a continuación, haga clic en **Ejecutar herramienta personalizada**.

     Ahora el sistema transforma la plantilla de texto y genera el archivo de salida correspondiente. No verá ningún error en la ventana **lista de errores** .
