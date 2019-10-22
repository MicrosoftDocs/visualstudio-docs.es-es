---
title: Aplicaciones de ejecución de Windows Store en el equipo local | Documentos de Microsoft
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196320"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Ejecutar aplicaciones de la Tienda Windows en el equipo local
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Solo se aplica a Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Para depurar, realizar pruebas o ejecutar análisis de rendimiento en una aplicación de la Tienda Windows, puede ejecutar la aplicación en el mismo equipo en el que se encuentre Visual Studio. Si la pantalla del dispositivo permite los toques, puede probar todas las funciones de la aplicación. De lo contrario, solo podrá usar gestos de mouse y teclado.  
  
## <a name="BKMK_In_this_topic"></a> En este tema  
 Puedes obtener información sobre:  
  
 [Cómo ejecutar en un equipo local](#BKMK_How_to_run_on_a_local_machine)  
  
 [Cómo cambiar entre una aplicación de Windows Store y Visual Studio en un solo monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="BKMK_How_to_run_on_a_local_machine"></a> Cómo ejecutar en un equipo local  
 Para ejecutar la aplicación en el equipo local, seleccione **máquina Local** en la lista desplegable situada junto al botón Iniciar depuración en el depurador **estándar** barra de herramientas.  
  
 ![Ejecutar en el equipo Local](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Si no ve el **estándar** barra de herramientas, haga clic en el **vista** menú, elija **las barras de herramientas**y, a continuación, haga clic en **estándar**.  
  
 La opción que seleccione en la lista desplegable permanece habilitada en el archivo de propiedades del proyecto y se convierte en el destino de ejecución predeterminado.  
  
 Además, puede establecer el destino de ejecución directamente en el archivo de propiedades del proyecto. Haga clic en el nombre del proyecto en **el Explorador de soluciones** y, a continuación, elija **propiedades**. Realice alguno de los siguientes procedimientos:  
  
- En los proyectos de C# y Visual Basic, haga clic en **depurar** y, a continuación, seleccione **máquina Local** desde el **dispositivo de destino** lista desplegable.  
  
     ![C&#35; y página de propiedades del proyecto de Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- En los proyectos de C++ y JavaScript, expanda el **propiedades de configuración** nodo, haga clic en **depuración**y, a continuación, seleccione **depurador Local de** desde el **depurador Para iniciar** lista.  
  
     ![C&#43; &#43; y página de propiedades del proyecto de JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Cómo cambiar entre una aplicación de Windows Store y Visual Studio en un solo monitor  
 **Para cambiar de una instancia en ejecución de una aplicación de Windows Store para Visual Studio**  
  
 Cuando ejecute una aplicación de la Tienda Windows en un equipo local y use un solo monitor, le recomendamos que vuelva a usar Visual Studio mientras se ejecute la aplicación. Por ejemplo, es posible que ningún punto de interrupción pueda llegar a la aplicación debido a que, por ejemplo, esté esperando un evento o se haya quedado bloqueada en un bucle infinito. Para cambiar a Visual Studio (presione Alt+Tab).
