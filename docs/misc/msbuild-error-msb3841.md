---
title: "Error de MSBuild MSB3841 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.ResolveSDKReference.InvalidDependencyInPlatform"
ms.assetid: 80ed22a1-bd62-4ace-892f-6b6009dff8e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Error de MSBuild MSB3841
**MSB3841: El SDK "{1}" depende del SDK "{0}", que no es compatible con proyectos destinados a la versión de la plataforma "{2}".**  
  
 MSBuild genera este error cuando el proyecto tiene una dependencia que no es compatible con la plataforma a la que está destinada su proyecto.  Usar dependencias incompatibles puede producir errores o comportamientos inesperados de la aplicación en el tiempo de ejecución  
  
### Para corregir este error para las referencias del proyecto  
  
1.  Los proyectos de Visual Basic, C\#, C\+\+ y JavaScript que tienen como destino proyectos de la Tienda de [!INCLUDE[win81](../debugger/includes/win81_md.md)] no pueden hacer referencia a proyectos de la Tienda Windows en C\+\+ que tienen como destino [!INCLUDE[win8](../debugger/includes/win8_md.md)], ya que esto daría lugar a problemas en tiempo de ejecución.  Si cualquier proyecto de la aplicación tiene como objetivo [!INCLUDE[win81](../debugger/includes/win81_md.md)] y la aplicación está compuesta por un proyecto en C\+\+ de la Tienda Windows, deberá realizar los pasos siguientes:  
  
2.  Redestinar todos los proyectos de la aplicación a [!INCLUDE[win81](../debugger/includes/win81_md.md)].  Para ello, haga doble clic con el botón secundario en cada uno de los proyectos de la aplicación, seleccione el comando **Redestinar a Windows 8.1** y haga clic en **Aceptar** en el cuadro de diálogo **Revisar cambios de proyecto y solución**.  
  
3.  Haga clic con el botón secundario en cada proyecto de Visual Basic, C\# y JavaScript que dependa de un proyecto en C\+\+ de la Tienda Windows, seleccione **Agregar referencia**, vaya a la ficha **Windows**, luego a la subficha **Extensiones**, desactive **Paquete en tiempo de ejecución de Microsoft Visual C\+\+ v11.0**, active **Paquete en tiempo de ejecución de Microsoft Visual C\+\+ v12.0** y, a continuación, haga clic en **Aceptar**.  
  
4.  Los proyectos de la Tienda Windows en Visual Basic, C\# y JavaScript que tienen como destino [!INCLUDE[win81](../debugger/includes/win81_md.md)] pueden hacer referencia a proyectos de la Tienda Windows en Visual Basic y C\#  que tienen como destino [!INCLUDE[win8](../debugger/includes/win8_md.md)] siempre que los proyectos de la Tienda de [!INCLUDE[win8](../debugger/includes/win8_md.md)] no usen ninguna API que haya quedado en desuso en [!INCLUDE[win81](../debugger/includes/win81_md.md)].  Vea [Migración de aplicaciones de la Tienda Windows a Windows 8.1](http://msdn.microsoft.com/library/windows/apps/dn263113.aspx) para determinar si los proyectos de la Tienda de [!INCLUDE[win8](../debugger/includes/win8_md.md)] seguirán comportándose según lo esperado cuando se haga referencia a ellos desde un proyecto de [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
     Los proyectos de la Tienda de [!INCLUDE[win8](../debugger/includes/win8_md.md)] no pueden depender de binarios o proyectos de la Tienda Windows que tienen como destino [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### Para corregir este error para las referencias del SDK de extensión  
  
1.  Los proyectos de la Tienda Windows en Visual Basic, C\#, C\+\+ y JavaScript que tienen como destino [!INCLUDE[win81](../debugger/includes/win81_md.md)] no puede hacer referencia a ningún SDK de extensión que dependa del paquete en tiempo de ejecución de Microsoft Visual C\+\+ v11.0, dado que esto dará lugar a problemas de tiempo de ejecución.  Para averiguar si un SDK de extensión depende del paquete en tiempo de ejecución de Microsoft Visual C\+\+ v11.0, cree un nuevo proyecto de Tienda Windows en C\#, haga clic con el botón secundario en el proyecto y seleccione **Agregar referencia**, vaya a la ficha **Windows** y luego a la subficha **Extensiones**, seleccione el SDK de extensión y vea si en el panel derecho del **Administrador de referencias** aparece **Microsoft.VCLibs, versión \= 11.0** como una dependencia.  
  
     Los proyectos de la Tienda Windows en Visual Basic, C\# y JavaScript que tienen como destino [!INCLUDE[win81](../debugger/includes/win81_md.md)] puede hacer referencia a SDK de extensión que no dependen del paquete en tiempo de ejecución de Microsoft Visual C\+\+ v11.0 siempre que estos SDK de extensión no utilicen las API que han quedado obsoletas en [!INCLUDE[win81](../debugger/includes/win81_md.md)].  Consulte el sitio del proveedor del SDK de extensión para determinar si se puede hacer referencia a él en proyectos de la Tienda que tengan como destino [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
     Si determina que el SDK de extensión al que la aplicación hace referencia no es compatible, debe realizar los pasos siguientes:  
  
2.  Consulte el nombre del proyecto que está provocando el error.  La plataforma de destino del proyecto se indica entre paréntesis junto al nombre del mismo.  Por ejemplo, **MyProjectName \(Windows 8.1\)** significa que el proyecto MyProjectName está destinado a la versión de la plataforma [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
3.  Vaya al sitio del proveedor del SDK de extensión no compatible e instale la versión del SDK de extensión con dependencias que son compatibles con la versión de la plataforma a la que está destinada su proyecto.  
  
4.  Si el SDK de extensión que instaló con anterioridad tiene dependencias de otros SDK de extensión, vaya a los sitios web de los proveedores de las dependencias e instale las versiones de estas dependencias que sean compatibles con la versión de la plataforma a la que está destinada su proyecto.  
  
    > [!NOTE]
    >  Si el proyecto tiene como destino [!INCLUDE[win81](../debugger/includes/win81_md.md)] y el SDK de extensión instalado anteriormente tiene una dependencia del paquete en tiempo de ejecución de Microsoft Visual C\+\+, la versión de dicho paquete que es compatible con Windows 8.1 es v12.0 y se instala con [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)].  
  
    > [!NOTE]
    >  Para averiguar si el SDK de extensión instalado anteriormente tiene dependencias de otros SDK de extensión, reinicie Visual Studio, cree un nuevo proyecto de la Tienda Windows en C\#, haga clic con el botón secundario en el proyecto y elija **Agregar referencia**, vaya a la ficha **Windows** y luego a la subficha **Extensiones**, seleccione el SDK de extensión y fíjese en el panel derecho del **Administrador de referencias**.  Si tiene dependencias, se mostrarán allí.  
  
5.  Reinicie Visual Studio y abra la aplicación.  
  
6.  Haga clic con el botón secundario en el proyecto que produce el error y elija **Agregar referencia** en el caso de proyectos en Visual Basic, C\# o JavaScript, o bien en **Referencias** en el caso de proyectos en C\+\+.  Para los proyectos en C\+\+, a continuación, haga clic en el botón Agregar nueva referencia.  
  
7.  Haga clic en la ficha **Windows** y luego en la subficha **Extensiones**.  Desactive las casillas que aparecen junto a los SDK de extensión antiguos y, a continuación, active las casillas que verá junto a los SDK de extensión nuevos.  Haga clic en **Aceptar**.