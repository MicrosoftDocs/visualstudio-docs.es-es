---
title: Codificación de una regla de validación personalizada para una prueba de rendimiento web en Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- custom validation rules
- validation rules, creating
- Web performance tests, creating custom validation rules
- rules, validation
- validation rules
ms.assetid: 989124bc-1a86-41f7-b37d-8f9e54dd4f0b
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c95e461f99a78a3241a091f7b590137e4dbc7066
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="coding-a-custom-validation-rule-for-a-web-performance-test"></a>Codificación de una regla de validación personalizada para una prueba de rendimiento web

Puede crear sus propias reglas de validación. Para ello, derive su propia clase de regla de una clase de regla de validación. Las reglas de la validación se derivan de la clase base <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>.

> [!NOTE]
> También puede crear reglas de extracción personalizadas. Para obtener más información, consulte [Crear código y complementos personalizados para las pruebas de carga](../test/create-custom-code-and-plug-ins-for-load-tests.md).

## <a name="to-create-custom-validation-rules"></a>Para crear reglas de validación personalizadas

1.  Abra un proyecto de prueba que contenga una prueba de rendimiento web.

2.  (Opcional) Cree un proyecto de bibliotecas de clases independiente para almacenar su regla de validación.

    > [!IMPORTANT]
    > Puede crear la clase en el mismo proyecto donde están sus pruebas. No obstante, si desea volver a usar la regla, es mejor crear un proyecto de biblioteca de clases diferente para almacenar la regla. Si crea un proyecto independiente, debe completar los pasos opcionales de este procedimiento.

3.  (Opcional) En el proyecto de bibliotecas de clases, agregue una referencia al archivo DLL Microsoft.VisualStudio.QualityTools.WebTestFramework.

4.  Cree una clase que se derive de la clase <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>. Implemente los miembros <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.Validate*> y <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule.RuleName*>.

5.  (Opcional) Compile el nuevo proyecto de biblioteca de clases.

6.  (Opcional) En el Proyecto de prueba, agregue una referencia al proyecto de bibliotecas de clases que contiene la regla de validación personalizada.

7.  En el Proyecto de prueba, abra una prueba de rendimiento web en el **Editor de prueba de rendimiento web**.

8.  Para agregar la regla de validación personalizada a una solicitud de prueba de rendimiento web, haga clic con el botón derecho en una solicitud y seleccione **Agregar regla de validación**.

     Aparecerá el cuadro de diálogo **Agregar regla de validación**. Verá su regla de validación personalizada en la lista **Seleccione una regla**, junto con las reglas de validación predefinidas. Seleccione su regla de validación personalizada y, a continuación, elija **Aceptar**.

9. Ejecute su prueba de rendimiento web.

## <a name="example"></a>Ejemplo

El código siguiente muestra una implementación de una regla de validación personalizada. Esta regla de validación imita el comportamiento de la regla de validación predefinida Etiqueta obligatoria. Utilice este ejemplo como punto de partida para sus propias reglas de validación personalizadas.

> [!WARNING]
> Las propiedades públicas en el código de un validador personalizado no pueden tener valores nulos.

```csharp
using System;
using System.Diagnostics;
using System.Globalization;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleWebTestRules
{
    //-------------------------------------------------------------------------
    // This class creates a custom validation rule named "Custom Validate Tag"
    // The custom validation rule is used to check that an HTML tag with a
    // particular name is found one or more times in the HTML response.
    // The user of the rule can specify the HTML tag to look for, and the
    // number of times that it must appear in the response.
    //-------------------------------------------------------------------------
    public class CustomValidateTag : ValidationRule
    {
        /// Specify a name for use in the user interface.
        /// The user sees this name in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleName
        {
            get { return "Custom Validate Tag"; }
        }

        /// Specify a description for use in the user interface.
        /// The user sees this description in the Add Validation dialog box.
        //---------------------------------------------------------------------
        public override string RuleDescription
        {
            get { return "Validates that the specified tag exists on the page."; }
        }

        // The name of the required tag
        private string RequiredTagNameValue;
        public string RequiredTagName
        {
            get { return RequiredTagNameValue; }
            set { RequiredTagNameValue = value; }
        }

        // The minimum number of times the tag must appear in the response
        private int MinOccurrencesValue;
        public int MinOccurrences
        {
            get { return MinOccurrencesValue; }
            set { MinOccurrencesValue = value; }
        }

        // Validate is called with the test case Context and the request context.
        // These allow the rule to examine both the request and the response.
        //---------------------------------------------------------------------
        public override void Validate(object sender, ValidationEventArgs e)
        {
            bool validated = false;
            int numTagsFound = 0;

            foreach (HtmlTag tag in e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName))
            {
                Debug.Assert(string.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase));

                if (++numTagsFound >= MinOccurrences)
                {
                    validated = true;
                    break;
                }
            }

            e.IsValid = validated;

            // If the validation fails, set the error text that the user sees
            if (!validated)
            {
                if (numTagsFound > 0)
                {
                    e.Message = String.Format("Only found {0} occurences of the tag", numTagsFound);
                }
                else
                {
                    e.Message = String.Format("Did not find any occurences of tag '{0}'", RequiredTagName);
                }
            }
        }
    }
}
```

```vb
Imports System
Imports System.Diagnostics
Imports System.Globalization
Imports Microsoft.VisualStudio.TestTools.WebTesting

Namespace SampleWebTestRules

    '-------------------------------------------------------------------------
    ' This class creates a custom validation rule named "Custom Validate Tag"
    ' The custom validation rule is used to check that an HTML tag with a
    ' particular name is found one or more times in the HTML response.
    ' The user of the rule can specify the HTML tag to look for, and the
    ' number of times that it must appear in the response.
    '-------------------------------------------------------------------------
    Public Class CustomValidateTag
        Inherits Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule

        ' Specify a name for use in the user interface.
        ' The user sees this name in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleName() As String
            Get
                Return "Custom Validate Tag"
            End Get
        End Property

        ' Specify a description for use in the user interface.
        ' The user sees this description in the Add Validation dialog box.
        '---------------------------------------------------------------------
        Public Overrides ReadOnly Property RuleDescription() As String
            Get
                Return "Validates that the specified tag exists on the page."
            End Get
        End Property

        ' The name of the required tag
        Private RequiredTagNameValue As String
        Public Property RequiredTagName() As String
            Get
                Return RequiredTagNameValue
            End Get
            Set(ByVal value As String)
                RequiredTagNameValue = value
            End Set
        End Property

        ' The minimum number of times the tag must appear in the response
        Private MinOccurrencesValue As Integer
        Public Property MinOccurrences() As Integer
            Get
                Return MinOccurrencesValue
            End Get
            Set(ByVal value As Integer)
                MinOccurrencesValue = value
            End Set
        End Property

        ' Validate is called with the test case Context and the request context.
        ' These allow the rule to examine both the request and the response.
        '---------------------------------------------------------------------
        Public Overrides Sub Validate(ByVal sender As Object, ByVal e As ValidationEventArgs)

            Dim validated As Boolean = False
            Dim numTagsFound As Integer = 0

            For Each tag As HtmlTag In e.Response.HtmlDocument.GetFilteredHtmlTags(RequiredTagName)

                Debug.Assert(String.Equals(tag.Name, RequiredTagName, StringComparison.InvariantCultureIgnoreCase))

                numTagsFound += 1
                If numTagsFound >= MinOccurrences Then

                    validated = True
                    Exit For
                End If
            Next

            e.IsValid = validated

            ' If the validation fails, set the error text that the user sees
            If Not (validated) Then
                If numTagsFound > 0 Then
                    e.Message = String.Format("Only found {0} occurences of the tag", numTagsFound)
                Else
                    e.Message = String.Format("Did not find any occurences of tag '{0}'", RequiredTagName)
                End If
            End If
        End Sub
    End Class
End Namespace
```

## <a name="see-also"></a>Vea también

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ValidationRule>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidateFormField>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleFindText>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequestTime>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredAttributeValue>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules.ValidationRuleRequiredTag>
- [Codificación de una regla de extracción personalizada para una prueba de rendimiento web](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)