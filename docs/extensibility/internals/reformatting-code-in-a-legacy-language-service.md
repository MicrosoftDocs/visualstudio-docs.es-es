---
title: "Cambiar el formato de código en un servicio de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 08d537f003279283509913d5f3d6aaa1bb1c4600
ms.openlocfilehash: d78fb976b3500a657d080634c6a041c218c3f1a1
ms.lasthandoff: 02/22/2017

---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Cambiar el formato de código en un servicio de lenguaje heredado

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] código fuente se puede volver a formatear por normalizar el uso de sangrías y espacio en blanco. Esto puede incluir insertar o quitar espacios o tabulaciones al principio de cada línea, agregar nuevas líneas entre las líneas o sustituir los espacios con tabulaciones o tabulaciones con espacios.  
  
>**Nota:** insertar o eliminar caracteres de nueva línea puede afectar a marcadores como puntos de interrupción y marcadores, pero agregar o quitar espacios o tabulaciones no afecta a los marcadores.  
  
Los usuarios pueden iniciar una operación de volver a seleccionando **la selección de formato** o **dar formato al documento** desde el **avanzadas** menú en el **editar** menú. Una operación de volver a también se desencadena cuando se inserta un fragmento de código o un carácter concreto. Por ejemplo, cuando se escribe una llave de cierre en C#, todo entre la llave de apertura correspondiente y la llave de cierre se aplica sangría automáticamente al nivel adecuado.
  
Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envía el **la selección de formato** o **dar formato al documento** comando al servicio de lenguaje, la <xref:Microsoft.VisualStudio.Package.ViewFilter>clase llama al <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método en la <xref:Microsoft.VisualStudio.Package.Source>clase.</xref:Microsoft.VisualStudio.Package.Source> </xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter> Para admitir el formato debe invalidar el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método y proporcione su propio formato de código.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  
  
## <a name="enabling-support-for-reformatting"></a>Habilitar la compatibilidad para volver a formatear  

Para admitir el formato, el `EnableFormatSelection` parámetro de la <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>debe establecerse en `true` al registrar el VSPackage.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Esto establece el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A>propiedad `true`.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> El <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>método devuelve el valor de esta propiedad.</xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> Si devuelve true, la <xref:Microsoft.VisualStudio.Package.ViewFilter>clase llama el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.ViewFilter>  
  
## <a name="implementing-reformatting"></a>Implementación de volver a formatear

Para implementar el cambio de formato, debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.Source>clase e invalidar el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> </xref:Microsoft.VisualStudio.Package.Source> El <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>objeto que describe el intervalo de formato y el <xref:Microsoft.VisualStudio.Package.EditArray>objeto contiene las modificaciones realizadas en el intervalo</xref:Microsoft.VisualStudio.Package.EditArray> </xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> Tenga en cuenta que este intervalo puede ser todo el documento. Sin embargo, puesto que es probable que se realizan varios cambios en el intervalo, todos los cambios deben ser reversibles en una única acción. Para ello, ajustar todos los cambios en un <xref:Microsoft.VisualStudio.Package.CompoundAction>objeto (consulte la sección "Uso de la clase CompoundAction" en este tema).</xref:Microsoft.VisualStudio.Package.CompoundAction>

### <a name="example"></a>Ejemplo  

En el ejemplo siguiente se garantiza que hay un espacio después de cada coma en la selección, a menos que el punto y coma seguida por un carácter de tabulación o al final de la línea. Espacios finales después de la última coma en una línea se eliminan. Consulte la sección "Utilizar la clase CompoundAction" en este tema para ver cómo se llama a este método desde el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>método.</xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>  

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
 
Todo el nuevo formato realizado en una sección de código debe ser reversible en una única acción. Esto puede realizarse mediante una <xref:Microsoft.VisualStudio.Package.CompoundAction>clase.</xref:Microsoft.VisualStudio.Package.CompoundAction> Esta clase contiene un conjunto de operaciones de edición en el búfer de texto en una operación de edición única.  
  
### <a name="example"></a>Ejemplo

Este es un ejemplo de cómo utilizar la <xref:Microsoft.VisualStudio.Package.CompoundAction>clase.</xref:Microsoft.VisualStudio.Package.CompoundAction> Vea el ejemplo en la sección "Implementación de compatibilidad de formato" en este tema para obtener un ejemplo de la `DoFormatting` (método).  
  
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
