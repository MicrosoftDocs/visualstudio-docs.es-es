---
title: 'Cómo: depurar código fuente de .NET Framework | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 250c2bd633a4f6c6b0580b23d0fbf1bb25094247
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566143"
---
# <a name="how-to-debug-net-framework-source"></a>Cómo: Depurar código fuente de .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: depurar el código de fuente de .NET Framework](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-dotnet-framework-source).  
  
La versión más reciente de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proporciona nuevas características para [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] depuración. Para depurar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origen, debe tener acceso a los símbolos de depuración para el código. También deberá habilitar ejecución paso a paso [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] origen.  
  
 Puede habilitar [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ejecución paso a paso y el símbolo que se descarga en el **opciones** cuadro de diálogo. Al habilitar la descarga de símbolos, puede descargarlos inmediatamente o habilitar la opción para una descarga posterior. Si no los descarga inmediatamente, los símbolos se descargarán la próxima vez que inicie la depuración de la aplicación. También puede hacer una descarga manual de la **módulos** ventana o el **pila de llamadas** ventana.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para habilitar la depuración de código fuente de .NET Framework  
  
1.  En el **herramientas** menú, haga clic en **opción**s.  
  
2.  En el **opciones** cuadro de diálogo, haga clic en el **depuración** categoría.  
  
3.  En el **General** , configure **habilitar .NET Framework** del origen de ejecución paso a paso.  
  
    1.  Si tenía habilitada la opción Sólo mi código , un cuadro de diálogo de advertencia le indicará que dicha opción se ha deshabilitado. Haga clic en **Aceptar**.  
  
    2.  Si no tenía una ubicación de caché de símbolos establecida, otro cuadro de diálogo de advertencia le indicará que se ha establecido una ubicación de caché de símbolos predeterminada. Haga clic en **Aceptar**.  
  
4.  En el **depuración** categoría, haga clic en **símbolos**.  
  
5.  Si desea cambiar la ubicación en caché de los símbolos:  
  
    1.  Abra el **depuración** nodo en el cuadro de la izquierda.  
  
    2.  En el **depuración** nodo, haga clic en **símbolos**.  
  
    3.  Editar la ubicación en **almacenar en caché los símbolos de servidores de símbolos a este directorio** o haga clic en **examinar** para elegir una ubicación.  
  
6.  Si desea descargar inmediatamente los símbolos, haga clic en **cargar símbolos de las ubicaciones indicadas**.  
  
     Este botón no está disponible en modo de diseño.  
  
     Si decide no descargar ahora los símbolos, estos se descargarán automáticamente la próxima vez que inicie la depuración del programa.  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para cargar símbolos de Framework mediante la ventana Módulos  
  
1.  En el **módulos** ventana, haga un módulo para el que no están cargados los símbolos. Puede indicar si los símbolos se cargan o no examinando el **símbolos estado** columna.  
  
2.  Seleccione **cargar símbolos desde** y haga clic en **servidores de símbolos de Microsoft** para descargar los símbolos desde el servidor de símbolos públicos de Microsoft o **ruta de acceso de símbolos** para cargarlos desde un directorio donde haya almacenado previamente los símbolos.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para cargar símbolos de Framework mediante la ventana Pila de llamadas  
  
1.  En el **pila de llamadas** ventana, haga un marco para el que no están cargados los símbolos. Este marco se oscurecerá.  
  
2.  Seleccione **cargar símbolos desde** y haga clic en **servidores de símbolos de Microsoft** o **ruta de acceso de símbolos**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Especificar archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



