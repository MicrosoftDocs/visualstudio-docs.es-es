---
title: Control glyph (VSPackage de control de código fuente) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0960209b67c8d2f111296840119807d95bb2e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538426"
---
# <a name="glyph-control-source-control-vspackage"></a>Control de glifo (VSPackage de control de código fuente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parte de la integración profunda disponible para los VSPackages de control de código fuente es la capacidad de mostrar sus propios glifos para indicar el estado de los elementos bajo control de código fuente.  
  
## <a name="levels-of-glyph-control"></a>Niveles de control de glifo  
 Un glifo de estado es un icono que indica el estado actual de un elemento cuando se muestra, por ejemplo, en **Explorador de soluciones** o en **vista de clases**. Un VSPackage de control de código fuente puede ejercitar dos niveles de control de glifo. Puede limitar la elección de glifos a un conjunto predefinido de glifos proporcionado por el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE, o puede definir un conjunto personalizado de glifos que se van a mostrar.  
  
### <a name="default-set-of-glyphs"></a>Conjunto predeterminado de glifos  
 Para determinar los glifos de estado asociados a un elemento en **Explorador de soluciones**, un proyecto solicita el glifo de estado del control de código fuente mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> . Un VSPackage de control de código fuente puede decidir mantener la elección de glifos limitado a los glifos predefinidos proporcionados por el IDE. En este caso, el VSPackage devuelve una matriz de valores que representan las enumeraciones de glifos que se definen en vsshell. idl. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Se trata de un conjunto predefinido de glifos establecido por el IDE, como un candado para el glifo "protegido" y una marca de verificación como el glifo "desprotegido".  
  
### <a name="custom-set-of-glyphs"></a>Conjunto personalizado de glifos  
 Un VSPackage de control de código fuente puede usar sus propios glifos para una "apariencia y funcionamiento" único cuando se instala. Cuando un VSPackage de control de código fuente nuevo está activo, debería poder comenzar a utilizar sus propios glifos incluso si un VSPackage de control de código fuente anterior todavía está cargado pero está inactivo. En este modo, el VSPackage de control de código fuente todavía puede usar los iconos existentes para mantener una apariencia coherente con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] si elige.  
  
 El <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servicio admite una interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> , que el VSPackage puede implementar opcionalmente y que el IDE solicitará. Cuando el IDE realiza una solicitud, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] intentará obtener esta interfaz a su vez desde el VSPackage de control de código fuente registrado actualmente. Si la interfaz existe en el VSPackage registrado, la solicitud del IDE para los glifos personalizados se realiza correctamente. de lo contrario, el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE utiliza su conjunto de glifos predeterminado.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>Utiliza el método [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para obtener una lista de imágenes que muestran distintos Estados de control de código fuente. El VSPackage de control de código fuente devuelve al IDE un identificador de la lista de imágenes para sus glifos personalizados. El IDE realiza una copia de la lista de imágenes en este momento y la usa más adelante para elegir los glifos que se van a mostrar. Si no se admite la nueva interfaz o el `IVsSccGlyphs::GetCustomGlyphList` método devuelve E_NOTIMPL, el IDE obtiene sus glifos de la lista predeterminada de glifos proporcionada por [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="see-also"></a>Consulte también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
