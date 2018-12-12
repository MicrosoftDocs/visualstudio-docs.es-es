---
title: Codificación de una regla de extracción personalizada para una prueba de rendimiento web
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- extraction rules
- Web performance tests, creating custom extraction rules
- extraction rules, creating custom
ms.assetid: 6bcc5712-6cc6-4f59-8933-6e8078318c45
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 41e9a025db4ec9c8425e0de6ba4ecad25f775d50
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066683"
---
# <a name="code-a-custom-extraction-rule-for-a-web-performance-test"></a>Codificar una regla de extracción personalizada para una prueba de rendimiento web

Puede crear sus propias reglas de extracción. Para ello, derive sus propias reglas de una clase de regla de extracción. Las reglas de extracción derivan de la clase base <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>.

> [!NOTE]
> También puede crear reglas de validación personalizadas. Para obtener más información, consulte [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-create-a-custom-extraction-rule"></a>Para crear una regla de extracción personalizada

1.  Abra un proyecto de prueba que contenga una prueba de rendimiento web.

2.  (Opcional) Cree un proyecto de bibliotecas de clases independiente para almacenar su regla de extracción.

    > [!IMPORTANT]
    > Puede crear la clase en el mismo proyecto donde están sus pruebas. No obstante, si desea volver a usar la regla, es mejor crear un proyecto de biblioteca de clases diferente para almacenar la regla. Si crea un proyecto independiente, debe completar los pasos opcionales de este procedimiento.

3.  (Opcional) En el proyecto de bibliotecas de clases, agregue una referencia a Microsoft.VisualStudio.QualityTools.WebTestFramework dll.

4.  Cree una clase que se derive de la clase <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>. Implemente los miembros <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> y <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.RuleName*>.

5.  (Opcional) Compile el nuevo proyecto de biblioteca de clases.

6.  (Opcional) En el proyecto de prueba, agregue una referencia al proyecto de bibliotecas de clases que contiene la regla de extracción personalizada.

7.  En el proyecto de prueba, abra una prueba de rendimiento web en el **Editor de pruebas de rendimiento web**.

8.  Para agregar la regla de extracción personalizada, haga clic con el botón derecho en una solicitud de prueba de rendimiento web y seleccione **Agregar regla de extracción**.

     Aparecerá el cuadro de diálogo **Agregar regla de extracción**. Verá su regla de validación personalizada en la lista **Seleccione una regla**, junto con las reglas de validación predefinidas. Seleccione su regla de extracción personalizada y, a continuación, elija **Aceptar**.

9. Ejecute su prueba de rendimiento web.

## <a name="example"></a>Ejemplo

El siguiente código muestra la implementación de una regla de extracción personalizada. Esta regla de extracción extrae el valor de un campo de entrada especificado. Utilice este ejemplo como punto de partida para sus propias reglas de extracción personalizadas.

```csharp
using System;
using System.Collections.Generic;
using Microsoft.VisualStudio.TestTools.WebTesting;
using System.Globalization;

namespace ClassLibrary2
{
    //-------------------------------------------------------------------------
    // This class creates a custom extraction rule named "Custom Extract Input"
    // The user of the rule specifies the name of an input field, and the
    // rule attempts to extract the value of that input field.
    //-------------------------------------------------------------------------
    public class CustomExtractInput : ExtractionRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Extract Input"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Extraction dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Extracts the value from a specified input field"; }
        }

        // The name of the desired input field
        private string NameValue;
        public string Name
        {
            get { return NameValue; }
            set { NameValue = value; }
        }

        // The Extract method.  The parameter e contains the web performance test context.
        //---------------------------------------------------------------------
        public override void Extract(object sender, ExtractionEventArgs e)
        {
            if (e.Response.HtmlDocument != null)
            {
                foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(new string[] { "input" }))
                {
                    if (String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase))
                    {
                        string formFieldValue = tag.GetAttributeValueAsString("value");
                        if (formFieldValue == null)
                        {
                            formFieldValue = String.Empty;
                        }

                        // add the extracted value to the web performance test context
                        e.WebTest.Context.Add(this.ContextParameterName, formFieldValue);
                        e.Success = true;
                        return;
                    }
                }
            }
            // If the extraction fails, set the error text that the user sees
            e.Success = false;
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name);
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports Microsoft.VisualStudio.TestTools.WebTesting
Imports System.Globalization

Namespace ClassLibrary2

    '-------------------------------------------------------------------------
    ' This class creates a custom extraction rule named "Custom Extract Input"
    ' The user of the rule specifies the name of an input field, and the
    ' rule attempts to extract the value of that input field.
    '-------------------------------------------------------------------------
    Public Class CustomExtractInput
        Inherits ExtractionRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Extract Input"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Extraction dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Extracts the value from a specified input field"
            End Get
        End Property

        ' The name of the desired input field
        Private NameValue As String
        Public Property Name() As String
            Get
                Return NameValue
            End Get
            Set(ByVal value As String)
                NameValue = value
            End Set
        End Property

        ' The Extract method.  The parameter e contains the web performance test context.
        '---------------------------------------------------------------------
        Public Overrides Sub Extract(ByVal sender As Object, ByVal e As ExtractionEventArgs)

            If Not e.Response.HtmlDocument Is Nothing Then

                For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(New String() {"input"})

                    If String.Equals(tag.GetAttributeValueAsString("name"), Name, StringComparison.InvariantCultureIgnoreCase) Then

                        Dim formFieldValue As String = tag.GetAttributeValueAsString("value")
                        If formFieldValue Is Nothing Then

                            formFieldValue = String.Empty
                        End If

                        ' add the extracted value to the web performance test context
                        e.WebTest.Context.Add(Me.ContextParameterName, formFieldValue)
                        e.Success = True
                        Return
                    End If
                Next
            End If
            ' If the extraction fails, set the error text that the user sees
            e.Success = False
            e.Message = String.Format(CultureInfo.CurrentCulture, "Not Found: {0}", Name)
        End Sub
    End Class
End Namespace
```

El método <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> contiene la funcionalidad básica de una regla de extracción. El método <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule.Extract*> del ejemplo anterior acepta <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionEventArgs>, que proporciona la respuesta generada por la solicitud que cubre esta regla de extracción. La respuesta contiene un <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument> que contiene todas las etiquetas de la respuesta. Las etiquetas de entrada se filtran de <xref:Microsoft.VisualStudio.TestTools.WebTesting.HtmlDocument>. Se examina cada etiqueta de entrada para ver si tiene un atributo llamado `name` cuyo valor equivale al valor de la propiedad `Name` proporcionado por el usuario. Si se encuentra una etiqueta con este atributo, se intenta extraer un valor incluido en el atributo `value` si existe un atributo de valor. En ese caso, se extraen el nombre y el valor de la etiqueta y se agregan al contexto de la prueba de rendimiento web. La regla de extracción pasa.

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHttpHeader>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractRegularExpression>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ExtractHiddenFields>
- [Codificación de una regla de validación personalizada para una prueba de rendimiento web](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)