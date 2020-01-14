---
title: 'Tutorial: conectar un host a un procesador de directivas generado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
ms.assetid: 254540d9-90d6-42de-8c1c-068affd56e83
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 17ec8199e99e76d5995e49570c82ad8523505ebe
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915989"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Tutorial: Conectar un host a un procesador de directivas personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede escribir su propio host que procesa plantillas de texto. En [Tutorial: crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md)se muestra un host personalizado básico. Podría extender ese host para agregar funciones como la generación de varios archivos de salida.

 En este tutorial, expandirá el host personalizado para que admita plantillas de texto que llamen a procesadores de directivas. Cuando se define un lenguaje específico de dominio, se genera un *procesador de directivas* para el modelo de dominio. El procesador de directivas facilita a los usuarios la escritura de plantillas que tienen acceso al modelo, lo que reduce la necesidad de escribir directivas de ensamblado e importación en las plantillas.

> [!WARNING]
> Este tutorial se basa en el [Tutorial: crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md). Realice ese tutorial primero.

 En este tutorial se incluyen las tareas siguientes:

- Usar [!INCLUDE[dsl](../includes/dsl-md.md)] para generar un procesador de directivas basado en un modelo de dominio.

- Conectar un host de plantilla de texto personalizado al procesador de directivas generado.

- Probar el host personalizado con el procesador de directivas generado.

## <a name="prerequisites"></a>Requisitos previos
 Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|SDK de visualización y modelado de Visual Studio|[Descarga del SDK de modelado](https://www.microsoft.com/download/details.aspx?id=48148)|

 Además, debe tener la transformación de plantilla de texto personalizado creada en [Tutorial: crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Usar Herramientas del lenguaje específico de dominio para generar un procesador de directivas
 En este tutorial, usará el Asistente para Diseñador de lenguaje específico de dominio para crear un lenguaje específico de dominio para la solución DSLMinimalTest.

#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>Para usar Herramientas del lenguaje específico de dominio para generar un procesador de directivas basado en un modelo de dominio

1. Cree una solución de lenguaje específico de dominio que tenga las siguientes características:

   - Nombre: DSLMinimalTest

   - Plantilla de solución: idioma mínimo

   - Extensión de archivo: min

   - Nombre de la compañía: fabrikam

     Para obtener más información sobre cómo crear una solución de lenguaje específico de dominio, consulte [Cómo: crear una solución de lenguaje específico de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. En el menú **Compilar** , haga clic en **Compilar solución**.

   > [!IMPORTANT]
   > Este paso genera el procesador de directivas y agrega la clave para él en el registro.

3. En el menú **Depurar**, haga clic en **Iniciar depuración**.

    Se abre una segunda instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

4. En la compilación experimental, en **Explorador de soluciones**, haga doble clic en el archivo **sample. min**.

    El archivo se abre en el diseñador. Observe que el modelo tiene dos elementos, ExampleElement1 y ExampleElement2, y un vínculo entre ellos.

5. Cierre la segunda instancia de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

6. Guarde la solución y, a continuación, cierre el Diseñador de lenguaje específico de dominio.

## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Conexión de un host de plantilla de texto personalizado a un procesador de directivas
 Después de generar el procesador de directivas, conecte el procesador de directivas y el host de plantilla de texto personalizado que creó en [Tutorial: crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md).

#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>Para conectar un host de plantilla de texto personalizado al procesador de directivas generado

1. Abra la solución CustomHost.

2. En el menú **Proyecto**, haga clic en **Agregar referencia**.

     Se abrirá el cuadro de diálogo **Agregar referencia** con la pestaña **.net** mostrada.

3. Agregue las siguientes referencias:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. En la parte superior de Program.cs o Module1. VB, agregue la siguiente línea de código:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Busque el código de la propiedad `StandardAssemblyReferences`y reemplácelo por el código siguiente:

    > [!NOTE]
    > En este paso, agregará referencias a los ensamblados necesarios para el procesador de directivas generado que el host admitirá.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6. Busque el código de la función `ResolveDirectiveProcessor`y reemplácelo por el código siguiente:

    > [!IMPORTANT]
    > Este código contiene referencias codificadas de forma rígida al nombre del procesador de directivas generado al que desea conectarse. Podría hacerlo con facilidad, en cuyo caso busca todos los procesadores de directivas que aparecen en el registro e intenta encontrar una coincidencia. En ese caso, el host funcionaría con cualquier procesador de directivas generado.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7. En el menú **Archivo**, haga clic en **Guardar todo**.

8. En el menú **Compilar** , haga clic en **Compilar solución**.

## <a name="testing-the-custom-host-with-the-directive-processor"></a>Probar el host personalizado con el procesador de directivas
 Para probar el host de plantilla de texto personalizado, primero debe escribir una plantilla de texto que llame al procesador de directivas generado. Después, ejecute el host personalizado, pásele el nombre de la plantilla de texto y compruebe que la Directiva se procesa correctamente.

#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Para crear una plantilla de texto para probar el host personalizado

1. Cree un archivo de texto y asígnele el nombre `TestTemplateWithDP.tt`. Puede usar cualquier editor de texto, como el Bloc de notas, para crear el archivo.

2. Agregue lo siguiente al archivo de texto:

    > [!NOTE]
    > No es necesario que el lenguaje de programación de la plantilla de texto coincida con el del host personalizado.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3. En el código, reemplace \<la ruta de acceso > con la ruta de acceso del archivo Sample. min del lenguaje específico del diseño que creó en el primer procedimiento.

4. Guarde y cierre el archivo.

#### <a name="to-test-the-custom-host"></a>Para probar el host personalizado

1. Abra una ventana Símbolo del sistema.

2. Escriba la ruta de acceso del archivo ejecutable del host personalizado, pero no presione ENTRAR todavía.

     Por ejemplo, escriba:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > En lugar de escribir la dirección, puede ir al archivo CustomHost. exe en el **Explorador de Windows**y, a continuación, arrastrar el archivo a la ventana del símbolo del sistema.

3. Escriba un espacio.

4. Escriba la ruta de acceso del archivo de plantilla de texto y, a continuación, presione ENTRAR.

     Por ejemplo, escriba:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > En lugar de escribir la dirección, puede ir al archivo TestTemplateWithDP. txt en el **Explorador de Windows**y, a continuación, arrastrar el archivo a la ventana del símbolo del sistema.

     La aplicación host personalizada se ejecuta e inicia el proceso de transformación de plantillas de texto.

5. En el **Explorador de Windows**, vaya a la carpeta que contiene el archivo TestTemplateWithDP. txt.

     La carpeta también contiene el archivo TestTemplateWithDP1. txt.

6. Abra este archivo para ver el resultados de la transformación de la plantilla de texto.

     Los resultados de la salida de texto generada aparecen y deben tener este aspecto:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Vea también
 [Tutorial: Crear un host de plantillas de texto personalizadas](../modeling/walkthrough-creating-a-custom-text-template-host.md)
