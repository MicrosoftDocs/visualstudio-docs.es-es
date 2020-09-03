---
title: Ejecutar aplicaciones de la tienda Windows en el equipo local | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196320"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Ejecutar aplicaciones de la Tienda Windows en el equipo local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Solo se aplica a Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Para depurar, realizar pruebas o ejecutar análisis de rendimiento en una aplicación de la Tienda Windows, puede ejecutar la aplicación en el mismo equipo en el que se encuentre Visual Studio. Si la pantalla del dispositivo permite los toques, puede probar todas las funciones de la aplicación. De lo contrario, solo podrá usar gestos de mouse y teclado.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> En este tema  
 Puedes obtener información sobre:  
  
 [Cómo ejecutar la aplicación en un equipo local](#BKMK_How_to_run_on_a_local_machine)  
  
 [Cómo cambiar de una aplicación de la Tienda Windows a Visual Studio en un solo monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Cómo ejecutar en un equipo local  
 Para ejecutar la aplicación en el equipo local, seleccione **equipo local** en la lista desplegable situada junto al botón iniciar depuración en la barra de herramientas **estándar** del depurador.  
  
 ![Ejecución en la máquina local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Si no puede ver la barra de herramientas **estándar** , haga clic en el menú **Ver** , seleccione **barras de herramientas**y, a continuación, haga clic en **estándar**.  
  
 La opción que seleccione en la lista desplegable permanece habilitada en el archivo de propiedades del proyecto y se convierte en el destino de ejecución predeterminado.  
  
 Además, puede establecer el destino de ejecución directamente en el archivo de propiedades del proyecto. Haga clic con el botón secundario en el nombre del proyecto en **Explorador de soluciones** y, a continuación, elija **propiedades**. Luego, realice una de las operaciones siguientes:  
  
- En proyectos de C# y Visual Basic, haga clic en **depurar** y, a continuación, seleccione **equipo local** en la lista desplegable **dispositivo de destino** .  
  
     ![&#35; y Visual Basic página de propiedades del proyecto](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- En proyectos de C++ y JavaScript, expanda el nodo **propiedades de configuración** , haga clic en **depuración**y seleccione **depurador local** en la lista **depurador para iniciar** .  
  
     ![Página de propiedades del proyecto de C&#43;&#43; y JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Cómo cambiar entre una aplicación de la tienda Windows y Visual Studio en un solo monitor  
 **Para cambiar de una instancia en ejecución de una aplicación de la Tienda Windows a Visual Studio**  
  
 Cuando ejecute una aplicación de la Tienda Windows en un equipo local y use un solo monitor, le recomendamos que vuelva a usar Visual Studio mientras se ejecute la aplicación. Por ejemplo, es posible que ningún punto de interrupción pueda llegar a la aplicación debido a que, por ejemplo, esté esperando un evento o se haya quedado bloqueada en un bucle infinito. Para cambiar a Visual Studio (presione Alt+Tab).
