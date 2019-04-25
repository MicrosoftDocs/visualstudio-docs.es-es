---
title: Control de glifo (VSPackage de Control de código fuente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f66613c5f5b8b6e48efda17330f66cdb87a06cf9
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613822"
---
# <a name="glyph-control-source-control-vspackage"></a>Control de glifo (VSPackage de control de código fuente)
Parte de la integración profunda disponible para VSPackages de control de código fuente es la capacidad para mostrar sus propios glifos para indicar el estado de los elementos bajo control de código fuente.

## <a name="levels-of-glyph-control"></a>Niveles de control de glifo
 Un glifo de estado es un icono que indica el estado actual de un elemento cuando se muestra, por ejemplo en **el Explorador de soluciones** o en **vista de clases**. Un VSPackage de control de código fuente puede ejercer dos niveles de control de glifo. Puede limitar la elección de glifos para un conjunto predefinido de glifos proporcionada por el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, o bien puede definir un conjunto personalizado de glifos para mostrarse.

### <a name="default-set-of-glyphs"></a>Conjunto predeterminado de glifos
 Para determinar los glifos de estado que están asociados con un elemento de **el Explorador de soluciones**, un proyecto solicita el glifo de estado de control de código fuente mediante el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>. Un control de código fuente VSPackage puede decidir mantener la elección de glifos limitado a los glifos predefinidos proporcionados por el IDE. En este caso, el VSPackage devuelve una matriz de valores que representan las enumeraciones de glifo que se definen en *vsshell.idl*. Para obtener más información, consulta <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Se trata de un conjunto predefinido de glifos establecido por el IDE, como un candado para el glifo protegidos y una marca de verificación para el glifo desprotegido.

### <a name="custom-set-of-glyphs"></a>Conjunto de glifos personalizados
 Un VSPackage de control de código fuente puede usar su propio glifos para un único aspecto cuando se instala. Cuando un control de código fuente nuevo VSPackage está activo, debe ser capaz de comenzar a usar su propio glifos incluso si VSPackage de control de un origen de la anterior todavía se carga pero inactiva. En este modo, el VSPackage de control de origen todavía puede usar los iconos existentes con el fin de mantener una apariencia coherente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si así lo decide.

 El <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> service admite una interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, que puede implementar opcionalmente el VSPackage y que le preguntará por el IDE. Cuando el IDE realiza una solicitud, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a su vez intenta obtener esta interfaz desde el control de origen actualmente registrado VSPackage. Si la interfaz existe en el VSPackage registrado, la solicitud del IDE de glifos personalizados se realiza correctamente; en caso contrario, el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE usa su conjunto predeterminado de los glifos.

 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> está usando el método [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para obtener una lista de imágenes que muestra el control de código fuente distintos Estados. El VSPackage de control de código fuente, devuelve al IDE de un identificador de la lista de imágenes para sus glifos personalizados. El IDE hace una copia de la lista de imágenes en este momento y usa más adelante para elegir los glifos para mostrarse. Si no se admite la nueva interfaz o `IVsSccGlyphs::GetCustomGlyphList` devuelve del método `E_NOTIMPL`, a continuación, el IDE obtiene sus glifos en la lista predeterminada de glifos proporcionado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>