---
title: 'Tutorial: Crear un procesador de directivas personalizado | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, custom directive processors
- walkthroughs [text templates], directive processor
ms.assetid: b8f35a36-14e1-4467-8f5f-e01402af14d5
caps.latest.revision: 74
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: eb2ab9d49cdeb1ed71da8ef67841f7796862dc30
ms.openlocfilehash: e27af2c3d824acd15a33cf1f452dcfa9ba2acf04
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-custom-directive-processor"></a>Tutorial: Crear un procesador de directivas personalizadas
*Procesadores de directivas* funcionan agregando código a la *clase de transformación generada*. Si se llama a un *directiva* de un *plantilla de texto*, el resto del código que escribe en la plantilla de texto puede basarse en la funcionalidad que proporciona la directiva.  
  
 Puede escribir sus propios procesadores de directivas personalizados. Esto le permite personalizar las plantillas de texto. Para crear un procesador de directivas personalizado, crea una clase que hereda de cualquiera <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>o <xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor>.</xref:Microsoft.VisualStudio.TextTemplating.RequiresProvidesDirectiveProcessor> </xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>  
  
 Las tareas que se ilustran en este tutorial son las siguientes:  
  
-   Crear un procesador de directivas personalizado  
  
-   Registrar el procesador de directivas  
  
-   Probar el procesador de directivas  
  
## <a name="prerequisites"></a>Requisitos previos  
 Para completar este tutorial, necesitará:  
  
-   Visual Studio 2010  
  
-   Visual Studio 2010 SDK  
  
## <a name="creating-a-custom-directive-processor"></a>Crear un procesador de directivas personalizado  
 En este tutorial, creará un procesador de directivas personalizado. Agregue una directiva personalizada que lee un archivo XML, se almacena en un <xref:System.Xml.XmlDocument>variable y lo expone a través de una propiedad.</xref:System.Xml.XmlDocument> En la sección "Probar el procesador de directivas", utilizará esta propiedad en una plantilla de texto para tener acceso al archivo XML.  
  
 La llamada a la directiva personalizada tiene un aspecto similar al siguiente:  
  
 `<#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<Your Path>DocFile.xml" #>`  
  
 El procesador de directivas personalizado agrega la variable y la propiedad a la clase de transformación generada. La directiva que escribe utiliza las <xref:System.CodeDom>clases para crear el código que el motor agrega a la clase de transformación generada.</xref:System.CodeDom> El <xref:System.CodeDom>clases crean código en Visual C# o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], según el idioma especificado en el `language` parámetro de la `template` directiva.</xref:System.CodeDom> El lenguaje del procesador de directivas y el lenguaje de la plantilla de texto que tiene acceso al procesador de directivas no tienen que coincidir.  
  
 El código que crea la directiva tiene un aspecto similar al siguiente:  
  
```c#  
private System.Xml.XmlDocument document0Value;  
  
public virtual System.Xml.XmlDocument Document0  
{  
  get  
  {  
    if ((this.document0Value == null))  
    {  
      this.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>);  
    }  
    return this.document0Value;  
  }  
}  
```  
  
```vb#  
Private document0Value As System.Xml.XmlDocument  
  
Public Overridable ReadOnly Property Document0() As System.Xml.XmlDocument  
    Get  
        If (Me.document0Value Is Nothing) Then  
            Me.document0Value = XmlReaderHelper.ReadXml(<FileNameParameterValue>)  
        End If  
        Return Me.document0Value  
    End Get  
End Property  
```  
  
#### <a name="to-create-a-custom-directive-processor"></a>Para crear un procesador de directivas personalizado  
  
1.  En Visual Studio, cree un proyecto de biblioteca de clases de Visual C# o Visual Basic con el nombre CustomDP.  
  
    > [!NOTE]
    >  Si desea instalar el procesador de directivas en más de un equipo, es mejor utilizar un proyecto de extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (VSIX) e incluir un archivo .pkgdef en la extensión. Para obtener más información, consulte [implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md).  
  
2.  Agregue referencias a estos ensamblados:  
  
    -   **Microsoft.VisualStudio.TextTemplating. \*.0**  
  
    -   **Microsoft.VisualStudio.TextTemplating.Interfaces. \*.0**  
  
3.  Reemplace el código de **Class1** con el código siguiente. Este código define una clase CustomDirectiveProcessor que hereda de la <xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>clase e implementa los métodos necesarios.</xref:Microsoft.VisualStudio.TextTemplating.DirectiveProcessor>  
  
    ```c#  
    using System;  
    using System.CodeDom;  
    using System.CodeDom.Compiler;  
    using System.Collections.Generic;  
    using System.Globalization;  
    using System.IO;  
    using System.Text;  
    using System.Xml;  
    using System.Xml.Serialization;  
    using Microsoft.VisualStudio.TextTemplating;  
  
    namespace CustomDP  
    {  
        public class CustomDirectiveProcessor : DirectiveProcessor  
        {  
            //this buffer stores the code that is added to the   
            //generated transformation class after all the processing is done   
            //---------------------------------------------------------------------  
            private StringBuilder codeBuffer;  
  
            //Using a Code Dom Provider creates code for the   
            //generated transformation class in either Visual Basic or C#.  
            //If you want your directive processor to support only one language, you  
            //can hard code the code you add to the generated transformation class.  
            //In that case, you do not need this field.  
            //--------------------------------------------------------------------------  
            private CodeDomProvider codeDomProvider;  
  
            //this stores the full contents of the text template that is being processed  
            //--------------------------------------------------------------------------  
            private String templateContents;  
  
            //These are the errors that occur during processing. The engine passes   
            //the errors to the host, and the host can decide how to display them,  
            //for example the the host can display the errors in the UI  
            //or write them to a file.  
            //---------------------------------------------------------------------  
            private CompilerErrorCollection errorsValue;  
            public new CompilerErrorCollection Errors  
            {  
                get { return errorsValue; }  
            }  
  
            //Each time this directive processor is called, it creates a new property.  
            //We count how many times we are called, and append "n" to each new  
            //property name. The property names are therefore unique.  
            //-----------------------------------------------------------------------------  
            private int directiveCount = 0;  
  
            public override void Initialize(ITextTemplatingEngineHost host)  
            {  
                //we do not need to do any initialization work  
            }  
  
            public override void StartProcessingRun(CodeDomProvider languageProvider, String templateContents, CompilerErrorCollection errors)  
            {  
                //the engine has passed us the language of the text template  
                //we will use that language to generate code later  
                //----------------------------------------------------------  
                this.codeDomProvider = languageProvider;  
                this.templateContents = templateContents;  
                this.errorsValue = errors;  
  
                this.codeBuffer = new StringBuilder();  
            }  
  
            //Before calling the ProcessDirective method for a directive, the   
            //engine calls this function to see whether the directive is supported.  
            //Notice that one directive processor might support many directives.  
            //---------------------------------------------------------------------  
            public override bool IsDirectiveSupported(string directiveName)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                if (string.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    return true;  
                }  
                return false;  
            }  
  
            public override void ProcessDirective(string directiveName, IDictionary<string, string> arguments)  
            {  
                if (string.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    string fileName;  
  
                    if (!arguments.TryGetValue("FileName", out fileName))  
                    {  
                        throw new DirectiveProcessorException("Required argument 'FileName' not specified.");  
                    }  
  
                    if (string.IsNullOrEmpty(fileName))  
                    {  
                        throw new DirectiveProcessorException("Argument 'FileName' is null or empty.");  
                    }  
  
                    //Now we add code to the generated transformation class.  
                    //This directive supports either Visual Basic or C#, so we must use the  
                    //System.CodeDom to create the code.  
                    //If a directive supports only one language, you can hard code the code.  
                    //--------------------------------------------------------------------------  
  
                    CodeMemberField documentField = new CodeMemberField();  
  
                    documentField.Name = "document" + directiveCount + "Value";  
                    documentField.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentField.Attributes = MemberAttributes.Private;  
  
                    CodeMemberProperty documentProperty = new CodeMemberProperty();  
  
                    documentProperty.Name = "Document" + directiveCount;  
                    documentProperty.Type = new CodeTypeReference(typeof(XmlDocument));  
                    documentProperty.Attributes = MemberAttributes.Public;  
                    documentProperty.HasSet = false;  
                    documentProperty.HasGet = true;  
  
                    CodeExpression fieldName = new CodeFieldReferenceExpression(new CodeThisReferenceExpression(), documentField.Name);  
                    CodeExpression booleanTest = new CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, new CodePrimitiveExpression(null));  
                    CodeExpression rightSide = new CodeMethodInvokeExpression(new CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", new CodePrimitiveExpression(fileName));  
                    CodeStatement[] thenSteps = new CodeStatement[] { new CodeAssignStatement(fieldName, rightSide) };  
  
                    CodeConditionStatement ifThen = new CodeConditionStatement(booleanTest, thenSteps);  
                    documentProperty.GetStatements.Add(ifThen);  
  
                    CodeStatement s = new CodeMethodReturnStatement(fieldName);  
                    documentProperty.GetStatements.Add(s);  
  
                    CodeGeneratorOptions options = new CodeGeneratorOptions();  
                    options.BlankLinesBetweenMembers = true;  
                    options.IndentString = "    ";  
                    options.VerbatimOrder = true;  
                    options.BracingStyle = "C";  
  
                    using (StringWriter writer = new StringWriter(codeBuffer, CultureInfo.InvariantCulture))  
                    {  
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options);  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options);  
                    }  
  
                }//end CoolDirective  
  
                //One directive processor can contain many directives.  
                //If you want to support more directives, the code goes here...  
                //-----------------------------------------------------------------  
                if (string.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) == 0)  
                {  
                    //code for SuperCoolDirective goes here...  
                }//end SuperCoolDirective  
  
                //Track how many times the processor has been called.  
                //-----------------------------------------------------------------  
                directiveCount++;  
  
            }//end ProcessDirective  
  
            public override void FinishProcessingRun()  
            {  
                this.codeDomProvider = null;  
  
                //important: do not do this:  
                //the get methods below are called after this method   
                //and the get methods can access this field  
                //-----------------------------------------------------------------  
                //this.codeBuffer = null;  
            }  
  
            public override string GetPreInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the start of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any pre-initialization, so we will just return "".  
                //-----------------------------------------------------------------  
                //GetPreInitializationCodeForProcessingRun runs before the   
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  
  
            public override string GetPostInitializationCodeForProcessingRun()  
            {  
                //Use this method to add code to the end of the   
                //Initialize() method of the generated transformation class.  
                //We do not need any post-initialization, so we will just return "".  
                //------------------------------------------------------------------  
                //GetPostInitializationCodeForProcessingRun runs after the  
                //Initialize() method of the base class.  
                //-----------------------------------------------------------------  
                return String.Empty;  
            }  
  
            public override string GetClassCodeForProcessingRun()  
            {  
                //Return the code to add to the generated transformation class.  
                //-----------------------------------------------------------------  
                return codeBuffer.ToString();  
            }  
  
            public override string[] GetReferencesForProcessingRun()  
            {  
                //This returns the references that we want to use when   
                //compiling the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need a reference to this assembly to be able to call   
                //XmlReaderHelper.ReadXml from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    this.GetType().Assembly.Location  
                };  
            }  
  
            public override string[] GetImportsForProcessingRun()  
            {  
                //This returns the imports or using statements that we want to   
                //add to the generated transformation class.  
                //-----------------------------------------------------------------  
                //We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                //from the generated transformation class.  
                //-----------------------------------------------------------------  
                return new string[]  
                {  
                    "System.Xml",  
                    "CustomDP"  
                };  
            }  
        }//end class CustomDirectiveProcessor  
  
        //-------------------------------------------------------------------------  
        // the code that we are adding to the generated transformation class   
        // will call this method  
        //-------------------------------------------------------------------------  
        public static class XmlReaderHelper  
        {  
            public static XmlDocument ReadXml(string fileName)  
            {  
                XmlDocument d = new XmlDocument();  
  
                using (XmlTextReader reader = new XmlTextReader(fileName))  
                {  
                    try  
                    {  
                        d.Load(reader);  
                    }  
                    catch (System.Xml.XmlException e)  
                    {  
                        throw new DirectiveProcessorException("Unable to read the XML file.", e);  
                    }  
                }  
                return d;  
            }  
        }//end class XmlReaderHelper  
    }//end namespace CustomDP  
    ```  
  
    ```vb#  
    Imports System  
    Imports System.CodeDom  
    Imports System.CodeDom.Compiler  
    Imports System.Collections.Generic  
    Imports System.Globalization  
    Imports System.IO  
    Imports System.Text  
    Imports System.Xml  
    Imports System.Xml.Serialization  
    Imports Microsoft.VisualStudio.TextTemplating  
  
    Namespace CustomDP  
  
        Public Class CustomDirectiveProcessor  
        Inherits DirectiveProcessor  
  
            'this buffer stores the code that is added to the   
            'generated transformation class after all the processing is done   
            '---------------------------------------------------------------  
            Private codeBuffer As StringBuilder  
  
            'Using a Code Dom Provider creates code for the  
            'generated transformation class in either Visual Basic or C#.  
            'If you want your directive processor to support only one language, you  
            'can hard code the code you add to the generated transformation class.  
            'In that case, you do not need this field.  
            '--------------------------------------------------------------------------  
            Private codeDomProvider As CodeDomProvider  
  
            'this stores the full contents of the text template that is being processed  
            '--------------------------------------------------------------------------  
            Private templateContents As String  
  
            'These are the errors that occur during processing. The engine passes   
            'the errors to the host, and the host can decide how to display them,  
            'for example the the host can display the errors in the UI  
            'or write them to a file.  
            '---------------------------------------------------------------------  
            Private errorsValue As CompilerErrorCollection  
            Public Shadows ReadOnly Property Errors() As CompilerErrorCollection  
                Get  
                    Return errorsValue  
                End Get  
            End Property  
  
            'Each time this directive processor is called, it creates a new property.  
            'We count how many times we are called, and append "n" to each new  
            'property name. The property names are therefore unique.  
            '--------------------------------------------------------------------------  
            Private directiveCount As Integer = 0  
  
            Public Overrides Sub Initialize(ByVal host As ITextTemplatingEngineHost)  
  
                'we do not need to do any initialization work  
            End Sub  
  
            Public Overrides Sub StartProcessingRun(ByVal languageProvider As CodeDomProvider, ByVal templateContents As String, ByVal errors As CompilerErrorCollection)  
  
                'the engine has passed us the language of the text template  
                'we will use that language to generate code later  
                '----------------------------------------------------------  
                Me.codeDomProvider = languageProvider  
                Me.templateContents = templateContents  
                Me.errorsValue = errors  
  
                Me.codeBuffer = New StringBuilder()  
            End Sub  
  
            'Before calling the ProcessDirective method for a directive, the   
            'engine calls this function to see whether the directive is supported.  
            'Notice that one directive processor might support many directives.  
            '---------------------------------------------------------------------  
            Public Overrides Function IsDirectiveSupported(ByVal directiveName As String) As Boolean  
  
                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  
  
                If String.Compare(directiveName, "SuperCoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
                    Return True  
                End If  
  
                Return False  
            End Function  
  
            Public Overrides Sub ProcessDirective(ByVal directiveName As String, ByVal arguments As IDictionary(Of String, String))  
  
                If String.Compare(directiveName, "CoolDirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
  
                    Dim fileName As String  
  
                    If Not (arguments.TryGetValue("FileName", fileName)) Then  
                        Throw New DirectiveProcessorException("Required argument 'FileName' not specified.")  
                    End If  
  
                    If String.IsNullOrEmpty(fileName) Then  
                        Throw New DirectiveProcessorException("Argument 'FileName' is null or empty.")  
                    End If  
  
                    'Now we add code to the generated transformation class.  
                    'This directive supports either Visual Basic or C#, so we must use the  
                    'System.CodeDom to create the code.  
                    'If a directive supports only one language, you can hard code the code.  
                    '--------------------------------------------------------------------------  
  
                    Dim documentField As CodeMemberField = New CodeMemberField()  
  
                    documentField.Name = "document" & directiveCount & "Value"  
                    documentField.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentField.Attributes = MemberAttributes.Private  
  
                    Dim documentProperty As CodeMemberProperty = New CodeMemberProperty()  
  
                    documentProperty.Name = "Document" & directiveCount  
                    documentProperty.Type = New CodeTypeReference(GetType(XmlDocument))  
                    documentProperty.Attributes = MemberAttributes.Public  
                    documentProperty.HasSet = False  
                    documentProperty.HasGet = True  
  
                    Dim fieldName As CodeExpression = New CodeFieldReferenceExpression(New CodeThisReferenceExpression(), documentField.Name)  
                    Dim booleanTest As CodeExpression = New CodeBinaryOperatorExpression(fieldName, CodeBinaryOperatorType.IdentityEquality, New CodePrimitiveExpression(Nothing))  
                    Dim rightSide As CodeExpression = New CodeMethodInvokeExpression(New CodeTypeReferenceExpression("XmlReaderHelper"), "ReadXml", New CodePrimitiveExpression(fileName))  
                    Dim thenSteps As CodeStatement() = New CodeStatement() {New CodeAssignStatement(fieldName, rightSide)}  
  
                    Dim ifThen As CodeConditionStatement = New CodeConditionStatement(booleanTest, thenSteps)  
                    documentProperty.GetStatements.Add(ifThen)  
  
                    Dim s As CodeStatement = New CodeMethodReturnStatement(fieldName)  
                    documentProperty.GetStatements.Add(s)  
  
                    Dim options As CodeGeneratorOptions = New CodeGeneratorOptions()  
                    options.BlankLinesBetweenMembers = True  
                    options.IndentString = "    "  
                    options.VerbatimOrder = True  
                    options.BracingStyle = "VB"  
  
                    Using writer As StringWriter = New StringWriter(codeBuffer, CultureInfo.InvariantCulture)  
  
                        codeDomProvider.GenerateCodeFromMember(documentField, writer, options)  
                        codeDomProvider.GenerateCodeFromMember(documentProperty, writer, options)  
                    End Using  
  
                End If  'CoolDirective  
  
                'One directive processor can contain many directives.  
                'If you want to support more directives, the code goes here...  
                '-----------------------------------------------------------------  
                If String.Compare(directiveName, "supercooldirective", StringComparison.OrdinalIgnoreCase) = 0 Then  
  
                    'code for SuperCoolDirective goes here  
                End If 'SuperCoolDirective  
  
                'Track how many times the processor has been called.  
                '-----------------------------------------------------------------  
                directiveCount += 1  
            End Sub 'ProcessDirective  
  
            Public Overrides Sub FinishProcessingRun()  
  
                Me.codeDomProvider = Nothing  
  
                'important: do not do this:  
                'the get methods below are called after this method   
                'and the get methods can access this field  
                '-----------------------------------------------------------------  
                'Me.codeBuffer = Nothing  
            End Sub  
  
            Public Overrides Function GetPreInitializationCodeForProcessingRun() As String  
  
                'Use this method to add code to the start of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any pre-initialization, so we will just return "".  
                '-----------------------------------------------------------------  
                'GetPreInitializationCodeForProcessingRun runs before the   
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  
  
            Public Overrides Function GetPostInitializationCodeForProcessingRun() As String  
  
                'Use this method to add code to the end of the   
                'Initialize() method of the generated transformation class.  
                'We do not need any post-initialization, so we will just return "".  
                '------------------------------------------------------------------  
                'GetPostInitializationCodeForProcessingRun runs after the  
                'Initialize() method of the base class.  
                '-----------------------------------------------------------------  
                Return String.Empty  
            End Function  
  
            Public Overrides Function GetClassCodeForProcessingRun() As String  
  
                'Return the code to add to the generated transformation class.  
                '-----------------------------------------------------------------  
                Return codeBuffer.ToString()  
            End Function  
  
            Public Overrides Function GetReferencesForProcessingRun() As String()  
  
                'This returns the references that we want to use when   
                'compiling the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need a reference to this assembly to be able to call   
                'XmlReaderHelper.ReadXml from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", Me.GetType().Assembly.Location}  
            End Function  
  
            Public Overrides Function GetImportsForProcessingRun() As String()  
  
                'This returns the imports or using statements that we want to   
                'add to the generated transformation class.  
                '-----------------------------------------------------------------  
                'We need CustomDP to be able to call XmlReaderHelper.ReadXml  
                'from the generated transformation class.  
                '-----------------------------------------------------------------  
                Return New String() {"System.Xml", "CustomDP"}  
            End Function  
        End Class 'CustomDirectiveProcessor  
  
        '--------------------------------------------------------------------------  
        ' the code that we are adding to the generated transformation class   
        ' will call this method  
        '--------------------------------------------------------------------------  
        Public Class XmlReaderHelper  
  
            Public Shared Function ReadXml(ByVal fileName As String) As XmlDocument  
  
                Dim d As XmlDocument = New XmlDocument()  
  
                Using reader As XmlTextReader = New XmlTextReader(fileName)  
  
                    Try  
                        d.Load(reader)  
  
                    Catch e As System.Xml.XmlException  
  
                        Throw New DirectiveProcessorException("Unable to read the XML file.", e)  
                    End Try  
                End Using  
  
                Return d  
            End Function  
        End Class 'XmlReaderHelper  
  
    End Namespace  
    ```  
  
4.  Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , abra el **proyecto** menú y haga clic en **propiedades de CustomDP**. En el **aplicación** ficha **espacio de nombres raíz**, elimine el valor predeterminado, `CustomDP`.  
  
5.  En el **archivo** menú, haga clic en **guardar todo**.  
  
6.  En el menú **Compilar** , haga clic en **Compilar solución**.  
  
### <a name="build-the-project"></a>Compilar el proyecto  
 Compile el proyecto. En el menú **Compilar** , haga clic en **Compilar solución**.  
  
## <a name="registering-the-directive-processor"></a>Registrar el procesador de directivas  
 Antes de que se puede llamar a una directiva desde una plantilla de texto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], debe agregar una clave del registro para el procesador de directivas.  
  
> [!NOTE]
>  Si desea instalar el procesador de directivas en más de un equipo, es mejor definir una extensión de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (VSIX) que incluya un archivo .pkgdef junto con el ensamblado. Para obtener más información, consulte [implementar un procesador de directivas personalizado](../modeling/deploying-a-custom-directive-processor.md).  
  
 Las claves para los procesadores de directivas se encuentran en la siguiente ubicación del Registro:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  
  
 Para los sistemas 64 bits, la ubicación del Registro es:  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\*.0\TextTemplating\DirectiveProcessors  
```  
  
 En esta sección, agregará una clave para el procesador de directivas personalizado en el Registro, en la misma ubicación.  
  
> [!CAUTION]
>  Una modificación incorrecta del Registro puede provocar daños graves en el sistema. Antes de efectuar cambios en el Registro, realice una copia de seguridad de la información importante del equipo.  
  
#### <a name="to-add-a-registry-key-for-the-directive-processor"></a>Para agregar una clave del Registro para el procesador de directivas  
  
1.  Ejecute el `regedit` comando mediante el menú Inicio o la línea de comandos.  
  
2.  Vaya a la ubicación **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**y haga clic en el nodo.  
  
     En los sistemas de 64 bits, utilice **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\\\*.0\TextTemplating\DirectiveProcessors**  
  
3.  Agregue una nueva clave con el nombre CustomDirectiveProcessor.  
  
    > [!NOTE]
    >  Este es el nombre que utilizará en el campo de procesador de las directivas personalizadas. Este nombre no tiene que coincidir con el nombre de la directiva, el nombre de la clase de procesador de directivas ni el espacio de nombres de procesador de directivas.  
  
4.  Agregue un nuevo valor de cadena denominado Class con un valor CustomDP.CustomDirectiveProcessor para el nombre de la nueva cadena.  
  
5.  Agregue un nuevo valor de cadena denominado CodeBase con un valor igual a la ruta de acceso de CustomDP.dll que creó anteriormente en este tutorial.  
  
     Por ejemplo, podría ser la ruta de acceso como `C:\UserFiles\CustomDP\bin\Debug\CustomDP.dll`.  
  
     La clave del Registro debe tener los siguientes valores:  
  
    |Nombre|Tipo|Datos|  
    |----------|----------|----------|  
    |(Predeterminado)|REG_SZ|(valor no establecido)|  
    |Clase|REG_SZ|CustomDP.CustomDirectiveProcessor|  
    |CodeBase|REG_SZ|**\<Ruta de acceso a la solución >**CustomDP\bin\Debug\CustomDP.dll|  
  
     Si ha colocado el ensamblado en la GAC, los valores deberían ser similares a los siguientes:  
  
    |Nombre|Tipo|Datos|  
    |----------|----------|----------|  
    |(Predeterminado)|REG_SZ|(valor no establecido)|  
    |Clase|REG_SZ|CustomDP.CustomDirectiveProcessor|  
    |Ensamblado|REG_SZ|CustomDP.dll|  
  
6.  Reinicie Visual Studio.  
  
## <a name="testing-the-directive-processor"></a>Probar el procesador de directivas  
 Para probar el procesador de directivas, debe escribir una plantilla de texto que lo llame.  
  
 En este ejemplo, la plantilla de texto llama a la directiva y le pasa en el nombre de un archivo XML que contiene documentación para un archivo de clase.
  
 La plantilla de texto, a continuación, utiliza el <xref:System.Xml.XmlDocument>propiedad que crea la directiva para navegar al XML e imprimir los comentarios de documentación.</xref:System.Xml.XmlDocument>  
  
#### <a name="to-create-an-xml-file-for-use-in-testing-the-directive-processor"></a>Para crear un archivo XML y usarlo para probar el procesador de directivas  
  
1.  Cree un archivo de texto denominado `DocFile.xml` con cualquier editor de texto (por ejemplo, el Bloc de notas).  
  
    > [!NOTE]
    >  Puede crear este archivo en cualquier ubicación (por ejemplo, C:\Test\DocFile.xml).  
  
2.  Agregue lo siguiente al archivo de texto:  
  
    ```  
    <?xml version="1.0"?>  
    <doc>  
        <assembly>  
            <name>xmlsample</name>  
        </assembly>  
        <members>  
            <member name="T:SomeClass">  
                <summary>Class level summary documentation goes here.</summary>  
                <remarks>Longer comments can be associated with a type or member through the remarks tag</remarks>  
            </member>  
            <member name="F:SomeClass.m_Name">  
                <summary>Store for the name property</summary>  
            </member>   
            <member name="M:SomeClass.#ctor">  
                <summary>The class constructor.</summary>   
            </member>  
            <member name="M:SomeClass.SomeMethod(System.String)">  
                <summary>Description for SomeMethod.</summary>  
                <param name="s">Parameter description for s goes here</param>  
                <seealso cref="T:System.String">You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.</seealso>  
            </member>  
            <member name="M:SomeClass.SomeOtherMethod">  
                <summary>Some other method.</summary>  
                <returns>Return results are described through the returns tag.</returns>  
                <seealso cref="M:SomeClass.SomeMethod(System.String)">Notice the use of the cref attribute to reference a specific method</seealso>  
            </member>  
            <member name="M:SomeClass.Main(System.String[])">  
                <summary>The entry point for the application.</summary>  
                <param name="args">A list of command line arguments</param>  
            </member>  
            <member name="P:SomeClass.Name">  
                <summary>Name property</summary>  
                <value>A value tag is used to describe the property value</value>  
            </member>  
        </members>  
    </doc>  
    ```  
  
3.  Guarde y cierre el archivo.  
  
#### <a name="to-create-a-text-template-to-test-the-directive-processor"></a>Para crear una plantilla de texto y probar el procesador de directivas  
  
1.  En Visual Studio, cree un proyecto de biblioteca de clases de Visual C# o Visual Basic con el nombre TemplateTest.  
  
2.  Agregue un nuevo archivo de plantilla de texto denominado TestDP.tt.  
  
3.  Asegúrese de que el **herramienta personalizada** propiedad de TestDP.tt está establecida en `TextTemplatingFileGenerator`.  
  
4.  Cambie el contenido de TestDP.tt al siguiente texto.  
  
    > [!NOTE]
    >  Asegúrese de reemplazar la cadena `YOUR PATH>` con la ruta de acceso al archivo DocFile.xml.  
  
     El lenguaje de la plantilla de texto no tiene que coincidir con el lenguaje del procesador de directivas.  
  
    ```c#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".txt" #>  
  
    <#  //This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  //Uncomment this line if you want to see the generated transformation class. #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  
  
    <#  //This will use the results of the directive processor. #>  
    <#  //The directive processor has read the XML and stored it in Document0. #>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  
  
        foreach (XmlNode member in node.ChildNodes)  
        {  
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  
  
            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
            }  
            WriteLine("");  
        }  
    #>  
  
    <#  //You can call the directive processor again and pass it a different file. #>  
    <# //@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\<Your Second File>" #>  
  
    <#  //To use the results of the second directive call, use Document1. #>  
    <#  
        //XmlNode node2 = Document1.DocumentElement.SelectSingleNode("members");  
  
        //...  
    #>  
    ```  
  
    ```vb#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".txt" #>  
  
    <#  'This will call the custom directive processor. #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  'Uncomment this line if you want to see the generated transformation class. #>  
    <#  'System.Diagnostics.Debugger.Break() #>  
  
    <#  'This will use the results of the directive processor. #>  
    <#  'The directive processor has read the XML and stored it in Document0. #>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  
  
        Dim member As XmlNode  
        For Each member In node.ChildNodes  
  
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  
  
            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
            Next  
  
            WriteLine("")  
        Next  
    #>  
  
    <#  'You can call the directive processor again and pass it a different file. #>  
    <# '@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFileTwo.xml" #>  
  
    <#  'To use the results of the second directive call, use Document1. #>  
    <#  
        'node = Document1.DocumentElement.SelectSingleNode("members")  
  
        '...  
    #>  
    ```  
  
    > [!NOTE]
    >  En este ejemplo, el valor del parámetro `Processor` es `CustomDirectiveProcessor`. El valor del parámetro `Processor` debe coincidir con el nombre de la clave del Registro del procesador.  
  
5.  En el **archivo** menú, haga clic en **guardar todo**.  
  
#### <a name="to-test-the-directive-processor"></a>Para probar el procesador de directivas  
  
1.  En **el Explorador de soluciones**, haga clic en TestDP.tt y, a continuación, haga clic en **ejecutar herramienta personalizada**.  
  
     Para [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] usuarios, TestDP.txt no aparezca en **el Explorador de soluciones** de forma predeterminada. Para mostrar todos los archivos asignados al proyecto, abra el **proyecto** menú y haga clic en **mostrar todos los archivos**.  
  
2.  En **el Explorador de soluciones**, expanda el nodo TestDP.txt y, a continuación, haga doble clic en TestDP.txt para abrirlo en el editor.  
  
     Aparece la salida de texto generada. La salida debe tener un aspecto parecido al siguiente:  
  
    ```  
       Name:  T:SomeClass  
    summary:  Class level summary documentation goes here.  
    remarks:  Longer comments can be associated with a type or member through the remarks tag  
  
       Name:  F:SomeClass.m_Name  
    summary:  Store for the name property  
  
       Name:  M:SomeClass.#ctor  
    summary:  The class constructor.  
  
       Name:  M:SomeClass.SomeMethod(System.String)  
    summary:  Description for SomeMethod.  
      param:  Parameter description for s goes here  
    seealso:  You can use the cref attribute on any tag to reference a type or member and the compiler will check that the reference exists.  
  
       Name:  M:SomeClass.SomeOtherMethod  
    summary:  Some other method.  
    returns:  Return results are described through the returns tag.  
    seealso:  Notice the use of the cref attribute to reference a specific method  
  
       Name:  M:SomeClass.Main(System.String[])  
    summary:  The entry point for the application.  
      param:  A list of command line arguments  
  
       Name:  P:SomeClass.Name  
    summary:  Name property  
      value:  A value tag is used to describe the property value  
    ```  
  
## <a name="adding-html-to-generated-text"></a>Agregar HTML a texto generado  
 Después de probar el procesador de directivas personalizado, es posible que desee agregar algún HTML al texto generado.  
  
#### <a name="to-add-html-to-the-generated-text"></a>Para agregar HTML al texto generado  
  
1.  Reemplace el código de TestDP.tt por el siguiente: El HTML se resalta. Asegúrese de reemplazar la cadena `YOUR PATH` con la ruta de acceso al archivo DocFile.xml.  
  
    > [!NOTE]
    >  Apertura adicionales \<# y cierre #> etiquetas separan el código de instrucción de las etiquetas HTML.  
  
    ```c#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" #>  
    <#@ output extension=".htm" #>  
  
    <#  //this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  //uncomment this line if you want to see the generated transformation class #>  
    <#  //System.Diagnostics.Debugger.Break(); #>  
  
    <html><body>  
  
    <#  //this will use the results of the directive processor #>  
    <#  //the directive processor has read the XML and stored it in Document0#>  
    <#  
        XmlNode node = Document0.DocumentElement.SelectSingleNode("members");  
  
        foreach (XmlNode member in node.ChildNodes)  
        {  
    #>  
    <h3>  
    <#      
            XmlNode name = member.Attributes.GetNamedItem("name");  
            WriteLine("{0,7}:  {1}", "Name", name.Value);  
    #>  
    </h3>  
    <#  
            foreach (XmlNode comment in member.ChildNodes)  
            {  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText);  
    #>  
    <br/>  
    <#  
            }  
        }  
    #>  
    </body></html>  
    ```  
  
    ```vb#  
    <#@ assembly name="System.Xml" #>  
    <#@ template debug="true" language="vb" #>  
    <#@ output extension=".htm" #>  
  
    <#  'this will call the custom directive processor #>  
    <#@ CoolDirective Processor="CustomDirectiveProcessor" FileName="<YOUR PATH>\DocFile.xml" #>  
  
    <#  'uncomment this line if you want to see the generated transformation class #>  
    <#  'System.Diagnostics.Debugger.Break() #>  
  
    <html><body>  
  
    <#  'this will use the results of the directive processor #>  
    <#  'the directive processor has read the XML and stored it in Document0#>  
    <#  
        Dim node as XmlNode = Document0.DocumentElement.SelectSingleNode("members")  
  
        Dim member As XmlNode  
        For Each member In node.ChildNodes  
    #>  
    <h3>  
    <#      
            Dim name As XmlNode = member.Attributes.GetNamedItem("name")  
            WriteLine("{0,7}:  {1}", "Name", name.Value)  
    #>  
    </h3>  
    <#  
            Dim comment As XmlNode  
            For Each comment In member.ChildNodes  
                WriteLine("{0,7}:  {1}", comment.Name, comment.InnerText)  
    #>  
    <br/>  
    <#  
            Next  
        Next  
    #>  
    </body></html>  
    ```  
  
2.  En el **archivo** menú, haga clic en **Guardar TestDP.txt**.  
  
3.  Para ver el resultado en un explorador, en **el Explorador de soluciones**, haga clic en TestDP.htm y haga clic en **ver en el explorador**.  
  
     El resultado debe ser igual que el texto original pero con el formato HTML aplicado. Todos los nombres de elemento deben aparecer en negrita.

