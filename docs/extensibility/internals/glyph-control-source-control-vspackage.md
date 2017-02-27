---
title: "Glifo Control (Control de c&#243;digo fuente VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "glifos, paquetes de control de código fuente"
  - "paquetes de control de código fuente, glifos"
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# Glifo Control (Control de c&#243;digo fuente VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La parte de la integración profunda disponibles para el control de origen VSPackages es la capacidad para mostrar sus propios glifos para indicar el estado de los elementos bajo control de código fuente.  
  
## Niveles de Control de glifo  
 Un glifo de estado es un icono que indica el estado actual de un elemento cuando se muestra, por ejemplo en **Explorador de soluciones** o en **Vista de clases**.  Un control de origen VSPackage puede realizar dos niveles de control del glifo.  Puede limitar la elección de glifos un conjunto predefinido de glifos proporcionados por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE, o puede definir un conjunto personalizado de glifos que se mostrarán.  
  
### Conjunto predeterminado de glifos  
 Para determinar los glifos de estado que están asociados a un elemento de **Explorador de soluciones**, solicite un proyecto el glifo del estado de control de origen utilizando el <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>.  Un control de origen VSPackage puede decidir mantener la selección de los glifos limitados a los glifos predefinidos proporcionados por el IDE.  En este caso, el paquete VSPackage pasa a la matriz de valores que representan las enumeraciones de glifo que se definen en vsshell.idl.  Para obtener más información, vea <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> . Éste es un conjunto predefinido de glifos establecidos por el IDE, como un candado para “protegido” glifo, y una marca de verificación como “comprobó el glifo Out”.  
  
### personalizado establecido de glifos  
 Un control de origen VSPackage puede utilizar sus propios glifos para un “apariencia único” cuando se instala.  Cuando un nuevo control de origen VSPackage está activo, debe poder iniciar con sus propios glifos incluso si un control de origen anterior VSPackage todavía se carga pero inactivo.  En este modo, el control de código fuente VSPackage todavía puede usar los iconos existentes para mantener una apariencia coherente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] si elige.  
  
 El servicio de <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> admite una interfaz, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>, que el Paquete puede implementar opcionalmente y que están ordenados por el IDE.  Si el IDE realiza una solicitud, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] a su vez intentará para obtener esta interfaz de control de código fuente actualmente registrado VSPackage.  Si la interfaz existe en el paquete VSPackage registrado, el orden del IDE glifos personalizados correctamente; si no, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa el IDE al conjunto predeterminado de glifos.  
  
 El método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A> es utilizado por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] para obtener una lista de imágenes que muestran los distintos estados de control de código fuente.  El control de código fuente VSPackage vuelve al IDE que un identificador a la imagen muestra para los glifos personalizados.  El IDE hace una copia de la imagen mostrada en este punto se utiliza después para elegir los glifos para mostrarse.  Si la nueva interfaz no se admite o el método de `IVsSccGlyphs::GetCustomGlyphList` devuelve E\_NOTIMPL, después el IDE obtiene los glifos de la lista predeterminada de glifos proporcionados por [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Vea también  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>