---
title: Procedimiento Depurar código fuente de .NET Framework | Microsoft Docs
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092115"
---
# <a name="how-to-debug-net-framework-source"></a>Procedimiento Depurar código fuente de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona nuevas características para [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] depuración. Para depurar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origen, debe tener acceso a los símbolos de depuración para el código. También deberá habilitar ejecución paso a paso [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origen.  
  
 Puede habilitar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ejecución paso a paso y el símbolo que se descarga en el **opciones** cuadro de diálogo. Al habilitar la descarga de símbolos, puede descargarlos inmediatamente o habilitar la opción para una descarga posterior. Si no los descarga inmediatamente, los símbolos se descargarán la próxima vez que inicie la depuración de la aplicación. También puede hacer una descarga manual de la **módulos** ventana o el **pila de llamadas** ventana.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para habilitar la depuración de código fuente de .NET Framework  
  
1. En el menú **Herramientas** , haga clic en **Opciones**.  
  
2. En el **opciones** cuadro de diálogo, haga clic en el **depuración** categoría.  
  
3. En el **General** , configure **habilitar .NET Framework** del origen de ejecución paso a paso.  
  
    1. Si tenía habilitada la opción Sólo mi código , un cuadro de diálogo de advertencia le indicará que dicha opción se ha deshabilitado. Haga clic en **Aceptar**.  
  
    2. Si no tenía una ubicación de caché de símbolos establecida, otro cuadro de diálogo de advertencia le indicará que se ha establecido una ubicación de caché de símbolos predeterminada. Haga clic en **Aceptar**.  
  
4. En el **depuración** categoría, haga clic en **símbolos**.  
  
5. Si desea cambiar la ubicación en caché de los símbolos:  
  
    1. Abra el **depuración** nodo en el cuadro de la izquierda.  
  
    2. En el **depuración** nodo, haga clic en **símbolos**.  
  
    3. Editar la ubicación en **almacenar en caché los símbolos de servidores de símbolos a este directorio** o haga clic en **examinar** para elegir una ubicación.  
  
6. Si desea descargar inmediatamente los símbolos, haga clic en **cargar símbolos de las ubicaciones indicadas**.  
  
     Este botón no está disponible en modo de diseño.  
  
     Si decide no descargar ahora los símbolos, estos se descargarán automáticamente la próxima vez que inicie la depuración del programa.  
  
7. Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para cargar símbolos de Framework mediante la ventana Módulos  
  
1. En el **módulos** ventana, haga un módulo para el que no están cargados los símbolos. Puede indicar si los símbolos se cargan o no examinando el **símbolos estado** columna.  
  
2. Seleccione **cargar símbolos desde** y haga clic en **servidores de símbolos de Microsoft** para descargar los símbolos desde el servidor de símbolos públicos de Microsoft o **ruta de acceso de símbolos** para cargarlos desde un directorio donde haya almacenado previamente los símbolos.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para cargar símbolos de Framework mediante la ventana Pila de llamadas  
  
1. En el **pila de llamadas** ventana, haga un marco para el que no están cargados los símbolos. Este marco se oscurecerá.  
  
2. Seleccione **cargar símbolos desde** y haga clic en **servidores de símbolos de Microsoft** o **ruta de acceso de símbolos**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
