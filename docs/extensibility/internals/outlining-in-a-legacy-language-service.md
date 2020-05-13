---
title: Esquema en un servicio de lenguaje heredado ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706811"
---
# <a name="outlining-in-a-legacy-language-service"></a>Esquematización en un servicio de lenguaje heredado
La esquematización permite contraer un programa complejo en una visión general o un esquema. Por ejemplo, en C- todos los métodos se pueden contraer en una sola línea, mostrando solo la firma del método. Además, las estructuras y clases se pueden contraer para mostrar solo los nombres de las estructuras y clases. Dentro de un único método, la lógica compleja se puede contraer para mostrar `foreach`el `if`flujo `while`general mostrando solo la primera línea de instrucciones como , , y .

 Los servicios de lenguaje heredados se implementan como parte de un VSPackage, pero la forma más reciente de implementar características de servicio de lenguaje es usar extensiones MEF. Para obtener más información, consulte [Tutorial: Esquema](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Le recomendamos que comience a usar la nueva API del editor lo antes posible. Esto mejorará el rendimiento de su servicio de lenguaje y le permitirá aprovechar las nuevas características del editor.

## <a name="enabling-support-for-outlining"></a>Habilitación del soporte para la esquematización
 La `AutoOutlining` entrada del Registro se establece en 1 para habilitar la esquematización automática. La esquematización automática configura un análisis de todo el origen cuando se carga o cambia un archivo para identificar las regiones ocultas y mostrar los glifos de esquematización. La esquematización también puede ser controlada manualmente por el usuario.

 El valor `AutoOutlining` de la entrada del <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> Registro se <xref:Microsoft.VisualStudio.Package.LanguagePreferences> puede obtener a través de la propiedad de la clase. La `AutoOutlining` entrada del Registro se puede inicializar <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> con un parámetro con nombre para el atributo (consulte [Registro de un servicio](../../extensibility/internals/registering-a-legacy-language-service1.md) de lenguaje heredado para obtener más información).

## <a name="the-hidden-region"></a>La región oculta
 Para proporcionar esquematización, el servicio de lenguaje debe admitir regiones ocultas. Se trata de intervalos de texto que se pueden expandir o contraer. Las regiones ocultas se pueden delimitar mediante símbolos de idioma estándar, como llaves o símbolos personalizados. Por ejemplo, C- `#region` / `#endregion` tiene un par que delimita una región oculta.

 Las regiones ocultas son administradas por <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> un administrador de regiones ocultas, que se expone como la interfaz.

 La esquematización <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> utiliza regiones ocultas de la interfaz y contienen el intervalo de la región oculta, el estado visible actual y el banner que se mostrará cuando se contraiga el intervalo.

 El analizador de servicios <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> de lenguaje utiliza el método para agregar una <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> nueva región oculta con el comportamiento predeterminado para las regiones ocultas, mientras que el método permite personalizar la apariencia y el comportamiento del esquema. Una vez que las regiones [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ocultas se asignan a la sesión de región oculta, administra las regiones ocultas para el servicio de lenguaje.

 Si necesita determinar cuándo se destruye la sesión de región oculta, se cambia una región oculta o debe asegurarse de que una región oculta determinada esté visible; debe derivar una clase <xref:Microsoft.VisualStudio.Package.Source> de la clase <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>e <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>invalidar <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>los métodos adecuados, , , y , respectivamente.

### <a name="example"></a>Ejemplo
 Este es un ejemplo simplificado de creación de regiones ocultas para todos los pares de llaves. Se supone que el lenguaje proporciona coincidencia de llaves y que las llaves que se van a coincidir incluyen al menos las llaves ( . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . Este enfoque es sólo para fines ilustrativos. Una implementación completa tendría un <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>manejo completo de los casos en . Este ejemplo también muestra <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> cómo `true` establecer la preferencia temporalmente. Una alternativa es `AutoOutlining` especificar el `ProvideLanguageServiceAttribute` parámetro con nombre en el atributo del paquete de idioma.

 En este ejemplo se supone que las reglas de C- para comentarios, cadenas y literales.

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
