---
title: "Esquematización en un servicio de lenguaje heredado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 76f47edd31892a98ec3235bfc4a00f5f2e647408
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="outlining-in-a-legacy-language-service"></a>Esquematización en un servicio de lenguaje heredado
Esquematización hace posible contraer un programa complejo en una información general o un esquema. Por ejemplo, en C# se pueden contraer todos los métodos en una sola línea, que muestra solo la firma del método. Además, las estructuras y clases se pueden contraer para mostrar solo los nombres de las clases y estructuras. Dentro de un único método, se puede contraer una lógica compleja para mostrar el flujo general mostrando solo la primera línea de instrucciones como `foreach`, `if`, y `while`.  
  
 Los servicios de lenguaje heredado se implementan como parte de un paquete VSPackage, pero la forma más reciente para implementar características del servicio de lenguaje es utilizar las extensiones MEF. Para obtener más información, consulte [Tutorial: esquematización](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Le recomendamos que empiece a usar el nuevo editor de API tan pronto como sea posible. Esto mejora el rendimiento de su servicio de lenguaje y le permiten aprovechar las nuevas características del editor.  
  
## <a name="enabling-support-for-outlining"></a>Habilitar la compatibilidad para la esquematización  
 El `AutoOutlining` entrada del registro se establece en 1 para habilitar la esquematización automática. La esquematización automática, se configura un análisis de todo el origen cuando se carga un archivo o se cambia para identificar regiones ocultas y mostrar los glifos de esquematización. Esquematización también puede controlarse manualmente por el usuario.  
  
 El valor de la `AutoOutlining` entrada del registro puede obtenerse a través de la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> propiedad en la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> clase. El `AutoOutlining` entrada del registro se puede inicializar con un parámetro con nombre para el <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atributo (consulte [registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md) para obtener más información).  
  
## <a name="the-hidden-region"></a>La región oculta  
 Para proporcionar la esquematización, el servicio de lenguaje debe admitir regiones ocultas. Se trata de intervalos de texto que puede expandir o contraer. Regiones ocultas se pueden delimitar mediante símbolos de lenguaje estándar, como las llaves, o símbolos personalizados. Por ejemplo, C# posee un `#region` / `#endregion` par que delimita la región oculta.  
  
 Regiones ocultas administradas por un administrador de región oculta que se expone como la <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfaz.  
  
 Esquematización utiliza regiones ocultas el <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interfaz y contener el intervalo de la región oculta, el estado de visibilidad actual y el título de la que se mostrará cuando se contrae el intervalo.  
  
 El analizador de servicio de lenguaje utiliza la <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> método para agregar una nueva área oculta con el comportamiento predeterminado para las regiones ocultas, mientras el <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> método le permite personalizar la apariencia y comportamiento del contorno. Una vez regiones ocultas se conceden a la sesión de la región oculta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] administra las regiones ocultas para el servicio de lenguaje.  
  
 Si tiene que determinar cuándo se destruye la sesión de la región oculta, se cambia una región oculta o necesario para asegurarse de que una determinada región oculta está visible; debe derivar una clase de la <xref:Microsoft.VisualStudio.Package.Source> clase e invalidar los métodos adecuados, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, y <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, respectivamente.  
  
### <a name="example"></a>Ejemplo  
 Este es un ejemplo simplificado de creación de zonas ocultas para todos los pares de llaves. Se supone que proporciona el lenguaje de coincidencia de llaves y que las llaves que se hacen coincidir incluyen al menos las llaves ({y}). Este enfoque es solo con fines ilustrativos. Una implementación completa tendría una control completa de casos de <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. En este ejemplo también muestra cómo establecer el <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferencia `true` temporalmente. Una alternativa consiste en especificar el `AutoOutlining` con el nombre de parámetro en el `ProvideLanguageServiceAttribute` atributo en el paquete de idioma.  
  
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
 [Características del servicio de lenguaje heredado](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrar un servicio de lenguaje heredado](../../extensibility/internals/registering-a-legacy-language-service1.md)