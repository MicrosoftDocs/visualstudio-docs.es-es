---
title: 'Cómo: depurar .NET Framework origen | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49b13b8406dc96e8e7ebe5e79e26c5da02e8a53a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205439"
---
# <a name="how-to-debug-net-framework-source"></a>Cómo: Depurar código fuente de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona nuevas características para la [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] depuración. Para depurar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] el código fuente, debe tener acceso a los símbolos de depuración para el código. También debe habilitar la ejecución paso a paso del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] código fuente.  
  
 Puede habilitar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] la ejecución paso a paso y la descarga de símbolos en el cuadro de diálogo **Opciones** . Al habilitar la descarga de símbolos, puede descargarlos inmediatamente o habilitar la opción para una descarga posterior. Si no los descarga inmediatamente, los símbolos se descargarán la próxima vez que inicie la depuración de la aplicación. También puede realizar una descarga manual desde la ventana **módulos** o la ventana **pila de llamadas** .  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para habilitar la depuración de código fuente de .NET Framework  
  
1. En el menú **Herramientas** , haga clic en **Opciones**.  
  
2. En el cuadro de diálogo **Opciones** , haga clic en la categoría **depuración** .  
  
3. En el cuadro **General** , establezca **Habilitar .NET Framework** ejecutar paso a paso el código fuente.  
  
    1. Si tenía habilitada la opción Sólo mi código , un cuadro de diálogo de advertencia le indicará que dicha opción se ha deshabilitado. Haga clic en **Aceptar**.  
  
    2. Si no tenía una ubicación de caché de símbolos establecida, otro cuadro de diálogo de advertencia le indicará que se ha establecido una ubicación de caché de símbolos predeterminada. Haga clic en **Aceptar**.  
  
4. En la categoría **depuración** , haga clic en **símbolos**.  
  
5. Si desea cambiar la ubicación en caché de los símbolos:  
  
    1. Abra el nodo **depuración** en el cuadro de la izquierda.  
  
    2. En el nodo **depuración** , haga clic en **símbolos**.  
  
    3. Edite la ubicación de **los símbolos de caché desde los servidores de símbolos a este directorio** o haga clic en **examinar** para elegir una ubicación.  
  
6. Si desea descargar símbolos inmediatamente, haga clic en **cargar símbolos con las ubicaciones anteriores**.  
  
     Este botón no está disponible en modo de diseño.  
  
     Si decide no descargar ahora los símbolos, estos se descargarán automáticamente la próxima vez que inicie la depuración del programa.  
  
7. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para cargar símbolos de Framework mediante la ventana Módulos  
  
1. En la ventana **módulos** , haga clic con el botón secundario en un módulo para el que no se cargan los símbolos. Puede saber si los símbolos se cargan o no examinando la columna Estado de los **símbolos** .  
  
2. Seleccione **cargar símbolos desde** y haga clic en **servidores de símbolos de Microsoft** para descargar símbolos del servidor de símbolos públicos de Microsoft o la ruta de acceso de **símbolos** para cargarlos desde un directorio en el que haya almacenado símbolos previamente.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para cargar símbolos de Framework mediante la ventana Pila de llamadas  
  
1. En la ventana **pila de llamadas** , haga clic con el botón secundario en un marco para el que no se cargan los símbolos. Este marco se oscurecerá.  
  
2. Seleccione **cargar símbolos desde** y haga clic en **servidores de símbolos de Microsoft** o ruta de acceso de **símbolos**.  
  
## <a name="see-also"></a>Consulte también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
