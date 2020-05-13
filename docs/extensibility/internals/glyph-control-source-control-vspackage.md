---
title: Control de pictogramas (Control de código fuente VSPackage) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708318"
---
# <a name="glyph-control-source-control-vspackage"></a>Control de pictograma (control de código fuente VSPackage)
Parte de la integración profunda disponible para el control de código fuente VSPackages es la capacidad de mostrar sus propios glifos para indicar el estado de los elementos bajo control de código fuente.

## <a name="levels-of-glyph-control"></a>Niveles de control de glifos
 Un glifo de estado es un icono que indica el estado actual de un elemento cuando se muestra, por ejemplo, en el **Explorador** de soluciones o en la vista de **clases**. Un control de código fuente VSPackage puede ejercer dos niveles de control de glifo. Puede limitar la elección de glifos a un conjunto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] predefinido de glifos proporcionado por el IDE, o puede definir un conjunto personalizado de glifos que se mostrarán.

### <a name="default-set-of-glyphs"></a>Conjunto predeterminado de glifos
 Para determinar los glifos de estado asociados a un elemento en el **Explorador** <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>de soluciones , un proyecto solicita el glifo de estado del control de código fuente mediante el archivo . Un control de código fuente VSPackage puede decidir mantener la elección de glifos limitados a glifos predefinidos proporcionados por el IDE. En este caso, el VSPackage devuelve una matriz de valores que representan las enumeraciones de glifo que se definen en *vsshell.idl*. Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>. Se trata de un conjunto predefinido de pictogramas establecido por el IDE, como un candado para el glifo protegido y una marca de verificación para el glifo desprotegido.

### <a name="custom-set-of-glyphs"></a>Conjunto personalizado de glifos
 Un control de código fuente VSPackage puede usar sus propios glifos para una apariencia única cuando se instala. Cuando un nuevo control de código fuente VSPackage está activo, debe ser capaz de empezar a usar sus propios glifos, incluso si un control de código fuente anterior VSPackage todavía está cargado pero inactivo. En este modo, el control de código fuente VSPackage todavía puede [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usar los iconos existentes con el fin de mantener un aspecto coherente con si lo desea.

 El <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> servicio admite <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>una interfaz, , que el VSPackage puede implementar opcionalmente y que se pedirá por el IDE. Cuando el IDE realiza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] una solicitud, a su vez intentará obtener esta interfaz desde el control de código fuente registrado actualmente VSPackage. Si la interfaz existe en el VSPackage registrado, la solicitud del IDE para glifos personalizados se realiza correctamente; de lo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contrario, el IDE utiliza su conjunto predeterminado de glifos.

 El <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> método se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utiliza para obtener una lista de imágenes que muestran varios estados de control de código fuente. El control de código fuente VSPackage devuelve al IDE un identificador a la lista de imágenes para sus glifos personalizados. El IDE realiza una copia de la lista de imágenes en este punto y la usa más adelante para elegir los glifos que se van a mostrar. Si no se admite la `IVsSccGlyphs::GetCustomGlyphList` nueva `E_NOTIMPL`interfaz o el método devuelve , el IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]obtiene sus glifos de la lista predeterminada de glifos proporcionados por .

## <a name="see-also"></a>Vea también
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
