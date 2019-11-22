---
title: 'Walkthrough: Connecting a Host to a Generated Directive Processor | Microsoft Docs'
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
ms.openlocfilehash: 10c9c6cfa1d8553c79b710239a99f8ea9e2438e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301277"
---
# <a name="walkthrough-connecting-a-host-to-a-generated-directive-processor"></a>Tutorial: Conectar un host a un procesador de directivas personalizadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

You can write your own host that processes text templates. A basic custom host is demonstrated in [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md). You could extend that host to add functions such as generating multiple output files.

 In this walkthrough, you expand your custom host so that it supports text templates that call directive processors. When you define a domain-specific language, it generates a *directive processor* for the domain model. The directive processor makes it easier for users to write templates that access the model, reducing the need to write assembly and import directives in the templates.

> [!WARNING]
> This walkthrough builds on [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md). Perform that walkthrough first.

 En este tutorial se incluyen las tareas siguientes:

- Using [!INCLUDE[dsl](../includes/dsl-md.md)] to generate a directive processor that is based on a domain model.

- Connecting a custom text template host to the generated directive processor.

- Testing the custom host with the generated directive processor.

## <a name="prerequisites"></a>Requisitos previos
 Para definir un DSL, debe tener instalados los siguientes componentes:

|||
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](https://go.microsoft.com/fwlink/?LinkId=185579)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](https://go.microsoft.com/fwlink/?LinkId=185580)|
|SDK de Visual Studio de visualización y modelado|[http://go.microsoft.com/fwlink/?LinkID=186128](https://go.microsoft.com/fwlink/?LinkID=186128)|

 In addition, you must have the custom text template transformation created in [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="using-domain-specific-language-tools-to-generate-a-directive-processor"></a>Using Domain-Specific Language Tools to Generate a Directive Processor
 In this walkthrough, you use the Domain-Specific Language Designer Wizard to create a domain-specific language for the solution DSLMinimalTest.

#### <a name="to-use-domain-specific-language-tools-to-generate-a-directive-processor-that-is-based-on-a-domain-model"></a>To use Domain-Specific Language Tools to generate a directive processor that is based on a domain model

1. Create a domain-specific language solution that has the following characteristics:

   - Name: DSLMinimalTest

   - Solution template: Minimal Language

   - File extension: min

   - Company name: Fabrikam

     For more information about creating a domain-specific language solution, see [How to: Create a Domain-Specific Language Solution](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. En el menú **Compilar** , haga clic en **Compilar solución**.

   > [!IMPORTANT]
   > This step generates the directive processor and adds the key for it in the registry.

3. En el menú **Depurar**, haga clic en **Iniciar depuración**.

    A second instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] opens.

4. In the experimental build, in **Solution Explorer**, double-click the file **sample.min**.

    The file opens in the designer. Notice that the model has two elements, ExampleElement1 and ExampleElement2, and a link between them.

5. Close the second instance of [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

6. Save the solution, and then close the Domain-Specific Language Designer.

## <a name="connecting-a-custom-text-template-host-to-a-directive-processor"></a>Connecting a Custom Text Template Host to a Directive Processor
 After you generate the directive processor, you connect the directive processor and the custom text template host that you created in [Walkthrough: Creating a Custom Text Template Host](../modeling/walkthrough-creating-a-custom-text-template-host.md).

#### <a name="to-connect-a-custom-text-template-host-to-the-generated-directive-processor"></a>To connect a custom text template host to the generated directive processor

1. Open the CustomHost solution.

2. En el menú **Proyecto**, haga clic en **Agregar referencia**.

     The **Add Reference** dialog box opens with the **.NET** tab displayed.

3. Add the following references:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. At the top of Program.cs or Module1.vb, add the following line of code:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Locate the code for the property `StandardAssemblyReferences`, and replace it with the following code:

    > [!NOTE]
    > In this step, you add references to the assemblies that are required by the generated directive processor that your host will support.

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

6. Locate the code for the function `ResolveDirectiveProcessor`, and replace it with the following code:

    > [!IMPORTANT]
    > This code contains hard-coded references to the name of the generated directive processor to which you want to connect. You could easily make this more general, in which case it looks for all directive processors listed in the registry and tries to find a match. In that case, the host would work with any generated directive processor.

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

## <a name="testing-the-custom-host-with-the-directive-processor"></a>Testing the Custom Host with the Directive Processor
 To test the custom text template host, first you must write a text template that calls the generated directive processor. Then you run the custom host, pass to it the name of the text template, and verify that the directive is processed correctly.

#### <a name="to-create-a-text-template-to-test-the-custom-host"></a>Para crear una plantilla de texto para probar el host personalizado

1. Create a text file, and name it `TestTemplateWithDP.tt`. You can use any text editor, such as Notepad, to create the file.

2. Agregue lo siguiente al archivo de texto:

    > [!NOTE]
    > The programming language of the text template does not need to match that of the custom host.

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

3. In the code, replace \<YOUR PATH> with the path of the Sample.min file from the design-specific language you created in the first procedure.

4. Guarde y cierre el archivo.

#### <a name="to-test-the-custom-host"></a>Para probar el host personalizado

1. Abra una ventana de símbolo del sistema.

2. Escriba la ruta de acceso del archivo ejecutable del host personalizado, pero no presione ENTRAR todavía.

     Por ejemplo, escriba:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Instead of typing the address, you can browse to the file CustomHost.exe in **Windows Explorer**, and then drag the file into the Command Prompt window.

3. Escriba un espacio.

4. Escriba la ruta de acceso del archivo de plantilla de texto y, a continuación, presione ENTRAR.

     Por ejemplo, escriba:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Instead of typing the address, you can browse to the file TestTemplateWithDP.txt in **Windows Explorer**, and then drag the file into the Command Prompt window.

     The custom host application runs and starts the text template transformation process.

5. In **Windows Explorer**, browse to the folder that contains the file TestTemplateWithDP.txt.

     The folder also contains the file TestTemplateWithDP1.txt.

6. Abra este archivo para ver el resultados de la transformación de la plantilla de texto.

     The results of the generated text output appears and should look like this:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Vea también
 [Tutorial: Crear un host de plantillas de texto personalizadas](../modeling/walkthrough-creating-a-custom-text-template-host.md)
