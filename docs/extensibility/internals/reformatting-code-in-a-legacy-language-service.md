---
title: Cambiar el formato de código en un servicio de lenguaje heredado | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 392afbafc2ce15dbf7ee347efdf24ce1f7fe2301
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31133201"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Cambiar el formato de código en un servicio de lenguaje heredado

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] puede puede cambiar el código fuente para normalizar el uso de sangrías y espacio en blanco. Esto puede incluir insertar o quitar espacios o tabulaciones al principio de cada línea, agregar nuevas líneas entre las líneas o reemplazar espacios con tabulaciones o tabulaciones con espacios.  
  
>**Nota:** insertar o eliminar caracteres de nueva línea puede afectar a los marcadores, como los puntos de interrupción y marcadores, pero agregar o quitar espacios ni tabulaciones no afecta a los marcadores.  
  
Los usuarios pueden iniciar una operación cambiando el formato seleccionando **la selección de formato** o **dar formato al documento** desde el **avanzadas** menú en el **editar**menú. También puede desencadenarse una operación cambiando el formato cuando se inserta un fragmento de código o un carácter determinado. Por ejemplo, cuando se escribe una llave de cierre en C#, lo que aparece entre la llave de apertura correspondiente y la llave de cierre se aplica sangría automáticamente al nivel adecuado.
  
Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envía el **la selección de formato** o **dar formato al documento** comando para el servicio de lenguaje, la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase llamadas el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método en la <xref:Microsoft.VisualStudio.Package.Source> clase. Para admitir el formato debe invalidar el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método y proporcionar su propio formato de código.  
  
## <a name="enabling-support-for-reformatting"></a>Habilitar la compatibilidad para volver a formatear  

Para admitir el formato, el `EnableFormatSelection` parámetro de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> debe establecerse en `true` al registrar el VSPackage. Esto establece la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> propiedad `true`. El <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> método devuelve el valor de esta propiedad. Si devuelve true, el <xref:Microsoft.VisualStudio.Package.ViewFilter> clase llamadas el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.  
  
## <a name="implementing-reformatting"></a>Implementar el cambio de formato

Para implementar el nuevo formato, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.Source> clase e invalidar el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método. El <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> objeto describe el intervalo que se va a dar formato y la <xref:Microsoft.VisualStudio.Package.EditArray> objeto contiene las modificaciones realizadas en el intervalo. Tenga en cuenta que este intervalo puede ser todo el documento. Sin embargo, puesto que es probable que se realizan varios cambios en el intervalo, todos los cambios deben ser reversibles en una sola acción. Para ello, incluir todos los cambios en un <xref:Microsoft.VisualStudio.Package.CompoundAction> objeto (consulte la sección "Uso de la clase CompoundAction" en este tema).

### <a name="example"></a>Ejemplo  

En el ejemplo siguiente se garantiza que hay un único espacio después de cada coma en la selección, a menos que el punto y coma seguida por un carácter de tabulación o al final de la línea. Espacios finales después de eliminar la última coma en una línea. Vea la sección "Utilizar la clase CompoundAction" en este tema para ver cómo se llama a este método desde el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método.  

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
  
## <a name="using-the-compoundaction-class"></a>Uso de la clase CompoundAction  
 
Todas la operación realiza en una sección de código debería ser reversible en una sola acción. Esto puede realizarse mediante un <xref:Microsoft.VisualStudio.Package.CompoundAction> clase. Esta clase ajusta a un conjunto de operaciones de edición en el búfer de texto en una operación de edición único.  
  
### <a name="example"></a>Ejemplo

Este es un ejemplo de cómo usar la <xref:Microsoft.VisualStudio.Package.CompoundAction> clase. Vea el ejemplo en la sección "Implementación de compatibilidad de formato" en este tema para obtener un ejemplo de la `DoFormatting` método.  
  
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

## <a name="see-also"></a>Vea también

[Características del servicio de lenguaje heredado](legacy-language-service-features1.md)