---
title: 'Tutorial: Depurar plantillas de texto que acceden a un modelo'
description: Proporciona información sobre cómo depurar una plantilla de texto que tiene acceso a un modelo.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: d39b1ac72210145cc1efa1c513b7f3b76d8c2e36
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388235"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Tutorial: Depurar una plantilla de texto que tiene acceso a un modelo
Al modificar o agregar plantillas de texto en una solución de lenguaje específico del dominio, puede producir errores cuando el motor transforma la plantilla en código fuente o cuando compila el código generado. En el siguiente tutorial se muestran algunas de las cosas que puede hacer para depurar una plantilla de texto.

> [!NOTE]
> Para obtener más información sobre las plantillas de texto en general, vea [Generación de código y plantillas de texto T4.](../modeling/code-generation-and-t4-text-templates.md) Para obtener más información sobre la depuración de plantillas de texto, [vea Tutorial: Depurar una plantilla de texto.](debugging-a-t4-text-template.md)

## <a name="creating-a-domain-specific-language-solution"></a>Crear una solución Domain-Specific language
 En este procedimiento, se crea una solución de lenguaje específica del dominio que tiene las siguientes características:

- Nombre: DebuggingTestLanguage

- Plantilla de solución: lenguaje mínimo

- Extensión de archivo: .ddd

- Nombre de la empresa: Fabrikam

  Para obtener más información sobre cómo crear una solución de lenguaje específico de dominio, vea [Cómo: Crear una solución Domain-Specific language](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Creación de una plantilla de texto
 Agregue una plantilla de texto a la solución.

#### <a name="to-create-a-text-template"></a>Para crear una plantilla de texto

1. Compile la solución y empiece a ejecutarla en el depurador. (En el menú **Compilar,** haga clic en **Recompilar solución** y, a continuación, en el **menú** Depurar, haga clic **en Iniciar depuración).** Una nueva instancia de Visual Studio abre el proyecto de depuración.

2. Agregue un archivo de texto `DebugTest.tt` denominado al proyecto de depuración.

3. Asegúrese de que la **propiedad Herramienta** personalizada de DebugTest.tt esté establecida en `TextTemplatingFileGenerator` .

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Directivas de depuración que acceden a un modelo desde una plantilla de texto
 Para poder acceder a un modelo desde las instrucciones y expresiones de una plantilla de texto, primero debe llamar a un procesador de directivas generado. Llamar al procesador de directivas generado hace que las clases del modelo estén disponibles para el código de plantilla de texto como propiedades. Para obtener más información, vea [Accessing Models from Text Templates](../modeling/accessing-models-from-text-templates.md).

 En los procedimientos siguientes, depurará un nombre de directiva incorrecto y un nombre de propiedad incorrecto.

#### <a name="to-debug-an-incorrect-directive-name"></a>Para depurar un nombre de directiva incorrecto

1. Reemplace el código de DebugTest.tt por el código siguiente:

    > [!NOTE]
    > El código contiene un error. Va a introducir el error para depurarlo.

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

2. En **Explorador de soluciones**, haga clic con el botón derecho en DebugTest.tt y, a continuación, haga clic **en Ejecutar herramienta personalizada**.

     La **ventana Lista de** errores muestra este error:

     **El procesador denominado "DebuggingTestLanguageDirectiveProcessor" no admite la directiva denominada "modelRoot". La transformación no se ejecutará.**

     En este caso, la llamada de directiva contiene un nombre de directiva incorrecto. Ha especificado como `modelRoot` nombre de directiva, pero el nombre de directiva correcto es `DebuggingTestLanguage` .

3. Haga doble clic en el error en la ventana **Lista de** errores para ir al código.

4. Para corregir el código, cambie el nombre de la directiva a `DebuggingTestLanguage` .

     El cambio está resaltado.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. En **Explorador de soluciones**, haga clic con el botón derecho en DebugTest.tt y, a continuación, haga clic **en Ejecutar herramienta personalizada**.

     Ahora, el sistema transforma la plantilla de texto y genera el archivo de salida correspondiente. No verá ningún error en la ventana **Lista de** errores.

#### <a name="to-debug-an-incorrect-property-name"></a>Para depurar un nombre de propiedad incorrecto

1. Reemplace el código de DebugTest.tt por el código siguiente:

    > [!NOTE]
    > El código contiene un error. Va a introducir el error para depurarlo.

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

2. En **Explorador de soluciones**, haga clic con el botón derecho en DebugTest.tt y, a continuación, haga clic **en Ejecutar herramienta personalizada**.

     Aparece **la ventana Lista** de errores y muestra uno de estos errores:

     (C#)

     **Compilación de la transformación: Microsoft.VisualStudio.TextTemplating \<GUID> . GeneratedTextTransformation' no contiene una definición para 'ExampleModel'**

     (Visual Basic)

     **Compilación de la transformación: 'ExampleModel' no es miembro de 'Microsoft.VisualStudio.TextTemplating \<GUID> . GeneratedTextTransformation'.**

     En este caso, el código de plantilla de texto contiene un nombre de propiedad incorrecto. Ha especificado como `ExampleModel` nombre de propiedad, pero el nombre de propiedad correcto es `LibraryModel` . Puede encontrar el nombre de propiedad correcto en el parámetro provides, como se muestra en el código siguiente:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Haga doble clic en el error en la ventana Lista de errores para ir al código.

4. Para corregir el código, cambie el nombre de la propiedad por `LibraryModel` en el código de plantilla de texto.

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

5. En **Explorador de soluciones**, haga clic con el botón derecho en DebugTest.tt y, a continuación, haga clic **en Ejecutar herramienta personalizada**.

     Ahora, el sistema transforma la plantilla de texto y genera el archivo de salida correspondiente. No verá ningún error en la ventana **Lista de** errores.
