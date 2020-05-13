---
title: Propiedades de documento sin cargo en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b3db7f4cfa45ea96e3da3056f39c2a5c78a25ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708968"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Propiedades de documento personalizadas en un servicio de lenguaje heredado
Las propiedades del documento [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se pueden mostrar en la ventana **Propiedades.** Los lenguajes de programación generalmente no tienen propiedades asociadas con archivos de origen individuales. Sin embargo, XML admite propiedades de documento que afectan a la codificación, el esquema y la hoja de estilos.

## <a name="discussion"></a>Discusión
 Si el lenguaje necesita propiedades de documento personalizadas, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.DocumentProperties> clase e implementar las propiedades necesarias en la clase derivada.

 Además, las propiedades del documento se almacenan normalmente en el propio archivo de origen. Esto requiere que el servicio de lenguaje analice la información de propiedad del archivo de origen para mostrarla en la ventana **Propiedades** y que actualice el archivo de origen cuando se realice un cambio en las propiedades del documento en la ventana **Propiedades.**

## <a name="customize-the-documentproperties-class"></a>Personalizar la clase DocumentProperties
 Para admitir propiedades de documento personalizadas, <xref:Microsoft.VisualStudio.Package.DocumentProperties> debe derivar una clase de la clase y agregar tantas propiedades como necesite. También debe proporcionar atributos de usuario para organizarlos en la pantalla de la ventana **Propiedades.** Si una propiedad `get` solo tiene un descriptor de acceso, se muestra como de solo lectura en la ventana **Propiedades.** Si una propiedad `get` `set` tiene ambos y descriptores de acceso, la propiedad también se puede actualizar en el **propiedades** ventana.

### <a name="example"></a>Ejemplo
 A continuación se muestra <xref:Microsoft.VisualStudio.Package.DocumentProperties>una clase de `Filename` `Description`ejemplo derivada de , que muestra dos propiedades y . Cuando se actualiza una propiedad, <xref:Microsoft.VisualStudio.Package.LanguageService> se llama a un método personalizado en la clase para escribir la propiedad en el archivo de origen.

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
 Para crear instancias de la clase <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> de propiedades de <xref:Microsoft.VisualStudio.Package.LanguageService> documento personalizada, debe <xref:Microsoft.VisualStudio.Package.DocumentProperties> invalidar el método en la versión de la clase para devolver una única instancia de la clase.

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

## <a name="properties-in-the-source-file"></a>Propiedades en el archivo de origen
 Dado que las propiedades del documento suelen ser específicas del archivo de origen, los valores se almacenan en el propio archivo de origen. Esto requiere la compatibilidad del analizador de lenguaje o del analizador para definir estas propiedades. Por ejemplo, las propiedades de un documento XML se almacenan en el nodo raíz. Los valores del nodo raíz se modifican cuando se cambian los valores de la ventana **Propiedades** y el nodo raíz se actualiza en el editor.

### <a name="example"></a>Ejemplo
 Este ejemplo almacena `Filename` `Description` las propiedades y en las dos primeras líneas del archivo de origen, incrustadas en un encabezado de comentario especial, como:

```
//!Filename = file.testext
//!Description = A sample file
```

 En este ejemplo se muestran los dos métodos necesarios para obtener y establecer las propiedades del documento de las dos primeras líneas del archivo de origen, así como cómo se actualizan las propiedades si el usuario modifica el archivo de origen directamente. El `SetPropertyValue` método del ejemplo que se muestra `TestDocumentProperties` aquí es el mismo al que se llama desde la clase, como se muestra en la sección *Personalizar la clase DocumentProperties.*

 En este ejemplo se utiliza el analizador para determinar el tipo de tokens en las dos primeras líneas. Este ejemplo es solo para fines ilustrativos. Un enfoque más típico de esta situación es analizar el archivo de origen en lo que se denomina un árbol de análisis donde cada nodo del árbol contiene información sobre un token determinado. El nodo raíz contendría las propiedades del documento.

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
