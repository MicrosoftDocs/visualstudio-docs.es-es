---
title: Conexión del host al procesador de directivas generado
description: Obtenga información sobre cómo puede expandir el host personalizado para que admita plantillas de texto que llamen a procesadores de directivas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: ed51688e5b65e34d7067963dbf7b839b1f022768
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388326"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Tutorial: Conectar un host a un procesador de directivas generadas

Puede escribir su propio host que procese plantillas de texto. Un host personalizado básico se muestra en [Tutorial: Crear un host de plantilla de texto personalizado](../modeling/walkthrough-creating-a-custom-text-template-host.md). Podría ampliar ese host para agregar funciones como generar varios archivos de salida.

En este tutorial, expandirá el host personalizado para que admita plantillas de texto que llamen a procesadores de directivas. Al definir un lenguaje específico del dominio, genera un procesador *de directivas* para el modelo de dominio. El procesador de directivas facilita a los usuarios la escritura de plantillas que acceden al modelo, lo que reduce la necesidad de escribir directivas de ensamblado e importación en las plantillas.

> [!NOTE]
> Este tutorial se basa en [Tutorial: Crear un host de plantilla de texto personalizado.](../modeling/walkthrough-creating-a-custom-text-template-host.md) Realice primero ese tutorial.

En este tutorial se incluyen las tareas siguientes:

- Usar [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] para generar un procesador de directivas basado en un modelo de dominio.

- Conexión de un host de plantilla de texto personalizado al procesador de directivas generado.

- Probar el host personalizado con el procesador de directivas generado.

## <a name="prerequisites"></a>Requisitos previos

Para definir un DSL, debe tener instalados los siguientes componentes:

| Componente | Vínculo |
|-|-|
| Programa para la mejora | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| SDK de Visual Studio de visualización y modelado | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Además, debe tener la transformación de plantilla de texto personalizado creada en [Tutorial: Crear un host de plantilla de texto personalizado.](../modeling/walkthrough-creating-a-custom-text-template-host.md)

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Usar Domain-Specific Language Tools para generar un procesador de directivas

En este tutorial, usará el Asistente Domain-Specific diseñador de lenguaje para crear un lenguaje específico del dominio para la solución DSLMinimalTest.

1. Cree una solución de lenguaje específico de dominio que tenga las siguientes características:

   - Nombre: DSLMinimalTest

   - Plantilla de solución: lenguaje mínimo

   - Extensión de archivo: min

   - Nombre de la empresa: Fabrikam

   Para obtener más información sobre cómo crear una solución de lenguaje específico de dominio, [vea Cómo: Crear una solución Domain-Specific language](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. En el menú **Compilar** , haga clic en **Compilar solución**.

   > [!IMPORTANT]
   > Este paso genera el procesador de directivas y agrega la clave para él en el Registro.

3. En el menú **Depurar**, haga clic en **Iniciar depuración**.

    Se abre una segunda instancia Visual Studio.

4. En la compilación experimental, en **Explorador de soluciones**, haga doble clic en el **archivo sample.min**.

    El archivo se abre en el diseñador. Observe que el modelo tiene dos elementos, ExampleElement1 y ExampleElement2, y un vínculo entre ellos.

5. Cierre la segunda instancia de Visual Studio.

6. Guarde la solución y, a continuación, cierre el diseñador Domain-Specific lenguaje.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Conexión de un host de plantilla de texto personalizado a un procesador de directivas

Después de generar el procesador de directivas, conecte el procesador de directivas y el host de plantilla de texto personalizado que creó en [Tutorial: Crear](../modeling/walkthrough-creating-a-custom-text-template-host.md)un host de plantilla de texto personalizado .

1. Abra la solución CustomHost.

2. En el menú **Proyecto**, haga clic en **Agregar referencia**.

     Se **abre el cuadro** de diálogo Agregar referencia con la pestaña **.NET** mostrada.

3. Agregue las siguientes referencias:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. En la parte superior de Program.cs o Module1.vb, agregue la siguiente línea de código:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Busque el código de la propiedad `StandardAssemblyReferences` y reemplázquelo por el código siguiente:

    > [!NOTE]
    > En este paso, agregará referencias a los ensamblados necesarios para el procesador de directivas generado que admitirá el host.

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

6. Busque el código de la función `ResolveDirectiveProcessor` y reemplázquelo por el código siguiente:

    > [!IMPORTANT]
    > Este código contiene referencias codificadas de forma fuerte al nombre del procesador de directivas generado al que desea conectarse. Puede hacerlo más general fácilmente, en cuyo caso busca todos los procesadores de directivas enumerados en el registro e intenta encontrar una coincidencia. En ese caso, el host funcionaría con cualquier procesador de directivas generado.

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

7. En el menú **Archivo** , haga clic en **Guardar todo**.

8. En el menú **Compilar**, haga clic en **Compilar solución**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Prueba del host personalizado con el procesador de directivas

Para probar el host de plantilla de texto personalizado, primero debe escribir una plantilla de texto que llame al procesador de directivas generado. A continuación, ejecute el host personalizado, pase a él el nombre de la plantilla de texto y compruebe que la directiva se procesa correctamente.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Creación de una plantilla de texto para probar el host personalizado

1. Cree un archivo de texto y asígámoslo `TestTemplateWithDP.tt` . Puede usar cualquier editor de texto, como el Bloc de notas, para crear el archivo.

2. Agregue lo siguiente al archivo de texto:

    > [!NOTE]
    > El lenguaje de programación de la plantilla de texto no necesita coincidir con el del host personalizado.

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

3. En el código, reemplace por la ruta de acceso del archivo Sample.min del lenguaje específico \<YOUR PATH> del diseño que creó en el primer procedimiento.

4. Guarde y cierre el archivo.

### <a name="test-the-custom-host"></a>Prueba del host personalizado

1. Abra una ventana de símbolo del sistema.

2. Escriba la ruta de acceso del archivo ejecutable del host personalizado, pero no presione ENTRAR todavía.

     Por ejemplo, escriba:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > En lugar de escribir la dirección, puede ir al archivo CustomHost.exe en Explorador de Windows y, **a** continuación, arrastrar el archivo a la ventana del símbolo del sistema.

3. Escriba un espacio.

4. Escriba la ruta de acceso del archivo de plantilla de texto y, a continuación, presione ENTRAR.

     Por ejemplo, escriba:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > En lugar de escribir la dirección, puede ir al archivo TestTemplateWithDP.txt en Explorador de Windows y, **a** continuación, arrastrar el archivo a la ventana del símbolo del sistema.

     La aplicación host personalizada se ejecuta e inicia el proceso de transformación de la plantilla de texto.

5. En **Explorador de Windows**, vaya a la carpeta que contiene el archivo TestTemplateWithDP.txt.

     La carpeta también contiene el archivo TestTemplateWithDP1.txt.

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

- [Tutorial: Crear un host de plantillas de texto personalizadas](../modeling/walkthrough-creating-a-custom-text-template-host.md)
