---
title: 'Tutorial: Conectar un host a un procesador de directivas personalizadas'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 5b5346f47d3dcb836a0e8eeef7d9b21bd55ccd07
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49896242"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Tutorial: Conectar un host a un procesador de directivas generadas

Puede escribir su propio host que procesa las plantillas de texto. Un host personalizado básico se muestra en [Tutorial: crear un Host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md). Puede ampliar ese host para agregar funciones como la generación de varios archivos de salida.

En este tutorial, expanda el host personalizado para que admita plantillas de texto que llamen a procesadores de directivas. Cuando se define un lenguaje específico de dominio, genera un *procesador de directivas* para el modelo de dominio. El procesador de directivas facilita a los usuarios escribir plantillas que obtener acceso al modelo, lo que reduce la necesidad de escribir el ensamblado e importar directivas en las plantillas.

> [!NOTE]
> En este tutorial se basa en [Tutorial: crear un Host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md). Realice primero ese tutorial.

En este tutorial se incluyen las tareas siguientes:

- Uso de [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para generar un procesador de directivas que se basa en un modelo de dominio.

- Conectar un host de plantilla de texto personalizado para el procesador de directivas personalizadas.

- Probar el host personalizado con el procesador de directivas personalizadas.

## <a name="prerequisites"></a>Requisitos previos

Para definir un DSL, debe tener instalados los siguientes componentes:


| | |
|-|-|
| Programa para la mejora | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| SDK de Visual Studio de visualización y modelado | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Además, debe tener la transformación de plantilla de texto personalizado creada en [Tutorial: crear un Host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Usar herramientas de lenguajes específicos de dominio para generar un procesador de directivas

En este tutorial, usará al Asistente del Diseñador de lenguaje específico de dominio para crear un lenguaje específico de dominio para la solución DSLMinimalTest.

1. Crear una solución de lenguaje específico de dominio que tiene las siguientes características:

   -   Nombre: DSLMinimalTest

   -   Plantilla de solución: lenguaje mínimo

   -   Extensión de archivo: min

   -   Nombre de la compañía: Fabrikam

   Para obtener más información acerca de cómo crear una solución de lenguaje específico de dominio, consulte [Cómo: crear soluciones de lenguajes específicos de dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. En el menú **Compilar** , haga clic en **Compilar solución**.

   > [!IMPORTANT]
   > Este paso genera el procesador de directivas y agrega la clave del registro para él.

3. En el menú **Depurar**, haga clic en **Iniciar depuración**.

    Se abre una segunda instancia de Visual Studio.

4. En la compilación experimental, en **el Explorador de soluciones**, haga doble clic en el archivo **sample.min**.

    El archivo se abre en el diseñador. Tenga en cuenta que el modelo tiene dos elementos, ExampleElement1 y ExampleElement2 y un vínculo entre ellas.

5. Cierre la segunda instancia de Visual Studio.

6. Guarde la solución y, a continuación, cierre el Diseñador de lenguaje específico de dominio.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Conectar un Host de plantilla de texto personalizado a un procesador de directivas

Después de generar el procesador de directivas, conecte el procesador de directivas y el host de plantilla de texto personalizado que creó en [Tutorial: crear un Host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md).

1.  Abra la solución de CustomHost.

2.  En el menú **Proyecto**, haga clic en **Agregar referencia**.

     El **Agregar referencia** abre el cuadro de diálogo con el **.NET** muestra la ficha.

3.  Agregue las siguientes referencias:

    -   Microsoft.VisualStudio.Modeling.Sdk.11.0

    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    -   Microsoft.VisualStudio.TextTemplating.11.0

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4.  En la parte superior de Program.cs o Module1.vb, agregue la siguiente línea de código:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5.  Busque el código para la propiedad `StandardAssemblyReferences`y reemplácelo por el código siguiente:

    > [!NOTE]
    > En este paso, agregue referencias a los ensamblados requeridos por el procesador de directivas personalizadas que será compatible con el host.

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

6.  Busque el código para la función `ResolveDirectiveProcessor`y reemplácelo por el código siguiente:

    > [!IMPORTANT]
    > Este código contiene referencias codificado de forma rígida en el nombre del procesador de directivas personalizadas a la que desea conectarse. Podría cometer fácilmente esto más general, en cuyo caso busca todos los procesadores de directivas aparece en el registro e intenta encontrar una coincidencia. En ese caso, el host podría funcionar con cualquier procesador de directivas personalizadas.

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

7.  En el **archivo** menú, haga clic en **guardar todo**.

8.  En el menú **Compilar** , haga clic en **Compilar solución**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Probar el Host con el procesador de directivas personalizado

Para probar el host de plantilla de texto personalizado, primero debe escribir una plantilla de texto que llama el procesador de directivas personalizadas. A continuación, ejecute el host personalizado, pasándole el nombre de la plantilla de texto y comprobar que la directiva se ha procesado correctamente.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Crear una plantilla de texto para probar el host personalizado

1.  Cree un archivo de texto y asígnele el nombre `TestTemplateWithDP.tt`. Puede usar cualquier editor de texto, como el Bloc de notas, para crear el archivo.

2.  Agregue lo siguiente al archivo de texto:

    > [!NOTE]
    > El lenguaje de programación de la plantilla de texto no es necesario que coincida con la del host personalizado.

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

3.  En el código, reemplace \<YOUR PATH > con la ruta de acceso del archivo Sample.min desde el lenguaje de diseño específico que creó en el primer procedimiento.

4.  Guarde y cierre el archivo.

### <a name="test-the-custom-host"></a>Probar el host personalizado

1.  Abra una ventana de símbolo del sistema.

2.  Escriba la ruta de acceso del archivo ejecutable del host personalizado, pero no presione ENTRAR todavía.

     Por ejemplo, escriba:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > En lugar de escribir la dirección, puede ir al archivo CustomHost.exe en **Windows Explorer**y, a continuación, arrastre el archivo a la ventana de símbolo del sistema.

3.  Escriba un espacio.

4.  Escriba la ruta de acceso del archivo de plantilla de texto y, a continuación, presione ENTRAR.

     Por ejemplo, escriba:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > En lugar de escribir la dirección, puede examinar el archivo TestTemplateWithDP.txt en **Windows Explorer**y, a continuación, arrastre el archivo a la ventana de símbolo del sistema.

     La aplicación host personalizada se ejecuta e inicia el proceso de transformación de plantillas de texto.

5.  En **Windows Explorer**, vaya a la carpeta que contiene el archivo TestTemplateWithDP.txt.

     La carpeta también contiene el archivo TestTemplateWithDP1.txt.

6.  Abra este archivo para ver el resultados de la transformación de la plantilla de texto.

     Los resultados de la salida de texto generado aparecerá y debe tener este aspecto:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Vea también

- [Tutorial: Crear un host de plantillas de texto personalizadas](../modeling/walkthrough-creating-a-custom-text-template-host.md)
