---
title: Propiedades de documento personalizadas en servicios de lenguaje heredados
description: Obtenga información sobre cómo crear propiedades de documento personalizadas que se muestran en la ventana Propiedades de Visual Studio, como parte de un servicio de lenguaje heredado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7a9bd5b41d1c04e52d16ecb2fc327e648d9f81aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902992"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Propiedades de documento personalizadas en un servicio de lenguaje heredado
Las propiedades del documento se pueden mostrar en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ventana **propiedades** . Normalmente, los lenguajes de programación no tienen propiedades asociadas a archivos de código fuente individuales. Sin embargo, XML admite propiedades de documento que afectan a la codificación, el esquema y la hoja de estilos.

## <a name="discussion"></a>Debate
 Si su lenguaje necesita propiedades de documento personalizadas, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> clase e implementar las propiedades necesarias en la clase derivada.

 Además, las propiedades de documento normalmente se almacenan en el propio archivo de código fuente. Esto requiere que el servicio de lenguaje analice la información de la propiedad del archivo de código fuente para que se muestre en la ventana **propiedades** y para actualizar el archivo de código fuente cuando se realice un cambio en las propiedades del documento en la ventana **propiedades** .

## <a name="customize-the-documentproperties-class"></a>Personalizar la clase DocumentProperties
 Para admitir las propiedades de documento personalizadas, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> clase y agregar tantas propiedades como necesite. También debe proporcionar atributos de usuario para organizarlos en la ventana **propiedades** Mostrar. Si una propiedad solo tiene un `get` descriptor de acceso, se muestra como de solo lectura en la ventana **propiedades** . Si una propiedad tiene `get` `set` descriptores de acceso y, la propiedad también se puede actualizar en la ventana **propiedades** .

### <a name="example"></a>Ejemplo
 Esta es una clase de ejemplo derivada de <xref:Microsoft.VisualStudio.Package.DocumentProperties> , que muestra dos propiedades, `Filename` y `Description` . Cuando se actualiza una propiedad, se llama a un método personalizado en la <xref:Microsoft.VisualStudio.Package.LanguageService> clase para escribir la propiedad en el archivo de código fuente.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>Crear una instancia de la clase DocumentProperties personalizada
 Para crear una instancia de la clase de propiedades de documento personalizadas, debe invalidar el <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> método en su versión de la <xref:Microsoft.VisualStudio.Package.LanguageService> clase para devolver una única instancia de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> clase.

### <a name="example"></a>Ejemplo

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>Propiedades del archivo de código fuente
 Como las propiedades del documento suelen ser específicas del archivo de código fuente, los valores se almacenan en el propio archivo de código fuente. Esto requiere compatibilidad desde el analizador de lenguaje o el escáner para definir estas propiedades. Por ejemplo, las propiedades de un documento XML se almacenan en el nodo raíz. Los valores del nodo raíz se modifican cuando se cambian los valores de la ventana **propiedades** y el nodo raíz se actualiza en el editor.

### <a name="example"></a>Ejemplo
 En este ejemplo se almacenan las propiedades `Filename` y `Description` en las dos primeras líneas del archivo de código fuente, incrustadas en un encabezado de comentario especial, como:

```
//!Filename = file.testext
//!Description = A sample file
```

 En este ejemplo se muestran los dos métodos necesarios para obtener y establecer las propiedades del documento a partir de las dos primeras líneas del archivo de código fuente, así como la forma en que se actualizan las propiedades si el usuario modifica el archivo de código fuente directamente. El `SetPropertyValue` método del ejemplo que se muestra aquí es el mismo que se llama desde la `TestDocumentProperties` clase, tal y como se muestra en la sección *Personalización de la clase DocumentProperties* .

 En este ejemplo se usa el escáner para determinar el tipo de tokens en las dos primeras líneas. Este ejemplo se utiliza únicamente con fines ilustrativos. Un enfoque más habitual para esta situación es analizar el archivo de origen en lo que se denomina un árbol de análisis, donde cada nodo del árbol contiene información sobre un token determinado. El nodo raíz contiene las propiedades del documento.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vea también
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
