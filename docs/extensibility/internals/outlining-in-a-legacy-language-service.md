---
title: Esquematización en un servicio de lenguaje heredado | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba6d709dae3b2a20332b3122585ad2060628016e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56601362"
---
# <a name="outlining-in-a-legacy-language-service"></a>Esquematización en un servicio de lenguaje heredado
Esquematización hace posible contraer un programa complejo en una descripción general o esquema. Por ejemplo, en C# se pueden contraer todos los métodos en una sola línea, que muestra solo la firma del método. Además, las estructuras y clases se pueden contraer para mostrar solo los nombres de las clases y estructuras. Dentro de un único método, se puede contraer una lógica compleja para mostrar el flujo general mostrando solo la primera línea de instrucciones como `foreach`, `if`, y `while`.

 Servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características de servicio de lenguaje es usar las extensiones MEF. Para obtener más información, consulte [Tutorial: Esquematización](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
>  Se recomienda que comience a usar el nuevo editor de API tan pronto como sea posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.

## <a name="enabling-support-for-outlining"></a>Habilitar la compatibilidad para la esquematización
 El `AutoOutlining` entrada del registro se establece en 1 para habilitar la esquematización automática. Esquematizar automáticamente configura un análisis de todo el origen cuando se carga un archivo o se puede cambiar con el fin de identificar las regiones ocultas y mostrar los glifos de esquematización. Esquematización también puede controlarse manualmente por el usuario.

 El valor de la `AutoOutlining` entrada del registro puede obtenerse a través de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> propiedad en el <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. El `AutoOutlining` entrada del registro se puede inicializar con un parámetro con nombre para el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo (consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obtener más información).

## <a name="the-hidden-region"></a>La región oculta
 Para proporcionar la esquematización, el servicio de lenguaje debe admitir las regiones ocultas. Estos son los intervalos de texto que puede expandir o contraer. Las regiones ocultas se pueden delimitar mediante símbolos de lenguaje estándar, como llaves, o símbolos personalizados. Por ejemplo, C# tiene un `#region` / `#endregion` par que delimita la región oculta.

 Las regiones ocultas son administradas por un administrador de la región oculta, que se expone como la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfaz.

 Esquematizar regiones ocultas utiliza el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interfaz y contener el intervalo de la pancarta que se mostrará cuando se contrae el intervalo, el estado de visibilidad actual y la región oculta.

 El analizador del servicio de lenguaje usa el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> método para agregar una nueva región oculta con el comportamiento predeterminado para las regiones ocultas, mientras que el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> método le permite personalizar la apariencia y comportamiento del contorno. Una vez que se asignan las regiones ocultas a la sesión de la región oculta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administra las regiones ocultas para el servicio de lenguaje.

 Si necesita determinar cuándo se destruye la sesión de región oculta, se cambia una región oculta, o deberá asegurarse de que una región oculta determinada es visible; debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.Source> clase e invalidar los métodos adecuados, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, y <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivamente.

### <a name="example"></a>Ejemplo
 Este es un ejemplo simplificado de creación de las regiones ocultas para todos los pares de llaves. Se supone que el lenguaje proporciona coincidencia de llaves y que las llaves que se debe coincidir al menos incluyen entre llaves ({y}). Este enfoque es solo con fines ilustrativos. Una implementación completa tendría un tratamiento completo de casos de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. En este ejemplo también muestra cómo establecer el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferencia `true` temporalmente. Una alternativa consiste en especificar el `AutoOutlining` con el nombre de parámetro en el `ProvideLanguageServiceAttribute` atributo en el paquete de idioma.

 En este ejemplo se da por supuesto reglas de C# para los comentarios, cadenas y literales.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Vea también
- [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)
- [Registro de un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)