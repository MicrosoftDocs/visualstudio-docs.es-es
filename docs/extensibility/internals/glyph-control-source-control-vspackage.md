---
title: Control de glifo (VSPackage de Control de código fuente) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c3787b0afad7f89743950a922d5b19c2d204bdd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130721"
---
# <a name="glyph-control-source-control-vspackage"></a>Control de glifo (VSPackage de Control de código fuente)
Parte de la integración profunda disponible para VSPackages de control de código fuente es la capacidad para mostrar sus propios glifos para indicar el estado de los elementos bajo control de código fuente.  
  
## <a name="levels-of-glyph-control"></a>Niveles de Control de glifo  
 Un glifo de estado es un icono que indica el estado actual de un elemento cuando muestra, por ejemplo en **el Explorador de soluciones** o en **vista de clases**. Un control de código fuente VSPackage puede tener dos niveles de control de glifo. Puede limitar las opciones de glifos para un conjunto predefinido de glifos proporcionada por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, o bien puede definir un conjunto personalizado de glifos para mostrarse.  
  
### <a name="default-set-of-glyphs"></a>Conjunto predeterminado de glifos  
 Para determinar los glifos de estado que están asociados a un elemento de **el Explorador de soluciones**, un proyecto solicita el glifo de estado de control de código fuente mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Un control de código fuente VSPackage puede decidir mantener la elección de glifos limitado a los glifos predefinidos proporcionados por el IDE. En este caso, el VSPackage pase una matriz de valores que representan las enumeraciones de glifo que se definen en vsshell.idl. Para obtener más información, consulte <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Se trata de un conjunto predefinido de glifos que se establece mediante el IDE, como un candado para el glifo "Checked In" y una marca de verificación como el glifo "Desproteger".  
  
### <a name="custom-set-of-glyphs"></a>Conjunto personalizado de glifos  
 Un control de código fuente VSPackage puede usar sus propio glifos para un único "aspecto" cuando se instala. Cuando un control de código fuente nuevo VSPackage está activo, debe ser puedan empezar a usar sus propio glifos incluso si un origen anterior controlar VSPackage se seguirá cargando pero inactiva. En este modo, el control de código fuente VSPackage todavía puede usar los iconos existentes con el fin de mantener una apariencia coherente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si así lo decide.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servicio admite una interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, que puede implementar opcionalmente el VSPackage y que le pedirán por el IDE. Cuando el IDE realiza una solicitud, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a su vez intentarán obtener esta interfaz desde el control de origen actualmente registrado VSPackage. Si la interfaz no existe en el VSPackage registrado, la solicitud del IDE de glifos personalizados se realiza correctamente; en caso contrario, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE usa su conjunto predeterminado de glifos.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> método lo usa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para obtener una lista de imágenes que muestra el control de código fuente distintos Estados. El control de código fuente VSPackage devuelve el IDE de un identificador de la lista de imágenes para sus glifos personalizados. El IDE realiza una copia de la lista de imágenes en este momento y utiliza más adelante para elegir los glifos para mostrarse. Si no se admite la nueva interfaz o la `IVsSccGlyphs::GetCustomGlyphList` método devuelve E_NOTIMPL, a continuación, el IDE obtiene sus glifos desde la lista predeterminada de glifos proporcionado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>