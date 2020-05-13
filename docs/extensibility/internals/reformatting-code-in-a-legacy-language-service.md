---
title: Reformateo de código en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705910"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>Cambio de formato de código en un servicio de lenguaje heredado

En [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el código fuente se puede volver a formatear normalizando el uso de sangrías y espacios en blanco. Esto puede incluir insertar o eliminar espacios o pestañas al principio de cada línea, agregar nuevas líneas entre líneas o reemplazar espacios por pestañas o pestañas por espacios.

> [!NOTE]
> Insertar o eliminar caracteres de nueva línea puede afectar a marcadores como puntos de interrupción y marcadores, pero agregar o quitar espacios o tabulaciones no afecta a los marcadores.

Los usuarios pueden iniciar una operación de reformateo seleccionando **Formato de selección** o Formato de **documento** en el menú **Avanzado** del menú **Edición.** Una operación de reformateo también se puede desencadenar cuando se inserta un fragmento de código o un carácter determinado. Por ejemplo, cuando se escribe una llave de cierre en C-, todo entre la llave abierta coincidente y la llave de cierre se aplica automáticamente al nivel adecuado.

Cuando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] envía el comando **Formato de selección** o Formato de **documento** al servicio de lenguaje, la <xref:Microsoft.VisualStudio.Package.ViewFilter> clase llama al <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método de la <xref:Microsoft.VisualStudio.Package.Source> clase. Para admitir el formato, debe invalidar el <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> método y proporcionar su propio código de formato.

## <a name="enabling-support-for-reformatting"></a>Habilitación de la compatibilidad con el formateo

Para admitir el `EnableFormatSelection` formato, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> el parámetro `true` de la debe establecerse en al registrar el VSPackage. Esto establece <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> la `true`propiedad en . El <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> método devuelve el valor de esta propiedad. Si devuelve true, <xref:Microsoft.VisualStudio.Package.ViewFilter> la <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>clase llama al archivo .

## <a name="implementing-reformatting"></a>Implementación del reformateo

Para implementar el reformateo, debe <xref:Microsoft.VisualStudio.Package.Source> derivar una <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> clase de la clase e invalidar el método. El <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> objeto describe el intervalo <xref:Microsoft.VisualStudio.Package.EditArray> para dar formato y el objeto contiene las ediciones realizadas en el intervalo. Tenga en cuenta que este intervalo puede ser el documento completo. Sin embargo, dado que es probable que se realicen varios cambios en el intervalo, todos los cambios deben ser reversibles en una sola acción. Para ello, ajuste todos <xref:Microsoft.VisualStudio.Package.CompoundAction> los cambios en un objeto (consulte la sección "Uso de la clase CompoundAction" en este tema).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se garantiza que hay un único espacio después de cada coma de la selección, a menos que la coma vaya seguida de una tabulación o esté al final de la línea. Se eliminan los espacios finales después de la última coma de una línea. Vea la sección "Uso de la clase CompoundAction" en este <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> tema para ver cómo se llama a este método desde el método.

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

Todo el reformateo realizado en una sección de código debe ser reversible en una sola acción. Esto se puede <xref:Microsoft.VisualStudio.Package.CompoundAction> lograr mediante una clase. Esta clase ajusta un conjunto de operaciones de edición en el búfer de texto en una sola operación de edición.

### <a name="example"></a>Ejemplo

Este es un ejemplo de <xref:Microsoft.VisualStudio.Package.CompoundAction> cómo utilizar la clase. Vea el ejemplo de la sección "Implementación de compatibilidad `DoFormatting` para el formato" de este tema para obtener un ejemplo del método.

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

- [Características del servicio de lenguaje heredado](legacy-language-service-features1.md)
