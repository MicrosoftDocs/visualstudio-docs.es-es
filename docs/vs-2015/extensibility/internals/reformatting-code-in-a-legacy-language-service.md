---
title: Volver a formatear el código en un servicio de lenguaje heredado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eb0dac5e1282d544df9c04bf4c12303fb391739d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842930"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Cambio de formato de código en un servicio de lenguaje heredado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el código fuente se puede cambiar el formato normalizando el uso de sangrías y espacios en blanco. Esto puede incluir la inserción o eliminación de espacios o tabulaciones al principio de cada línea, la adición de nuevas líneas entre líneas o el reemplazo de espacios con tabulaciones o tabulaciones con espacios.  
  
> [!NOTE]
> **Nota:** La inserción o eliminación de caracteres de nueva línea puede afectar a marcadores como puntos de interrupción y marcadores, pero agregar o quitar espacios o tabulaciones no afecta a los marcadores.  
  
 Los usuarios pueden iniciar una operación de cambio de formato seleccionando **formato de selección** o **formato de documento** en el menú **Opciones avanzadas** del menú **edición** . También se puede desencadenar una operación de cambio de formato cuando se inserta un fragmento de código o un carácter determinado. Por ejemplo, cuando se escribe una llave de cierre en C#, se aplica automáticamente una sangría a todo lo que se encuentra entre la llave de apertura correspondiente y la llave de cierre hasta el nivel adecuado.  
  
 Cuando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] envía el comando **Format Selection** o **Format Document** al servicio de lenguaje, la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase llama al <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase. Para admitir el formato, debe invalidar el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método y proporcionar su propio código de formato.  
  
## <a name="enabling-support-for-reformatting"></a>Habilitar la compatibilidad para volver a formatear  
 Para admitir el formato, el `EnableFormatSelection` parámetro de <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> debe establecerse en `true` al registrar el VSPackage. Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> propiedad en `true` . El <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> método devuelve el valor de esta propiedad. Si devuelve true, la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase llama a <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .  
  
## <a name="implementing-reformatting"></a>Implementar volver a formatear  
 Para implementar el cambio de formato, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.Source> clase e invalidar el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método. El <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> objeto describe el intervalo al que se va a dar formato y el <xref:Microsoft.VisualStudio.Package.EditArray> objeto contiene las modificaciones realizadas en el intervalo. Tenga en cuenta que este intervalo puede ser todo el documento. Sin embargo, dado que es probable que se realicen varios cambios en el intervalo, todos los cambios deben ser reversibles en una única acción. Para ello, ajuste todos los cambios en un <xref:Microsoft.VisualStudio.Package.CompoundAction> objeto (consulte la sección "uso de la clase CompoundAction" de este tema).  
  
### <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se asegura de que haya un solo espacio después de cada coma de la selección, a menos que la coma vaya seguida de una tabulación o esté al final de la línea. Se eliminan los espacios finales situados después de la última coma en una línea. Vea la sección "uso de la clase CompoundAction" en este tema para ver cómo se llama a este método desde el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>Usar la clase CompoundAction  
 Todo el cambio de formato realizado en una sección de código debe ser reversible en una sola acción. Esto puede realizarse mediante una <xref:Microsoft.VisualStudio.Package.CompoundAction> clase. Esta clase ajusta un conjunto de operaciones de edición en el búfer de texto en una sola operación de edición.  
  
### <a name="example"></a>Ejemplo  
 A continuación se muestra un ejemplo de cómo usar la <xref:Microsoft.VisualStudio.Package.CompoundAction> clase. Vea el ejemplo de la sección "implementación de la compatibilidad con el formato" de este tema para obtener un ejemplo del `DoFormatting` método.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte también  
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
