---
title: Ejecutar aplicaciones UWP en el equipo local | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 08e0108a3fb7a93dc19fe1aa96988912068ace70
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>Ejecutar aplicaciones UWP en el equipo local
![Solo se aplica a Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Para depurar, probar o ejecutar análisis de rendimiento en una aplicación UWP, puede ejecutar la aplicación en el mismo equipo que hospeda Visual Studio. Si la pantalla del dispositivo permite los toques, puede probar todas las funciones de la aplicación. De lo contrario, solo podrá usar gestos de mouse y teclado.  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>Cómo ejecutar en un equipo local  
 Para ejecutar la aplicación en el equipo local, seleccione **equipo Local** en la lista desplegable situada junto al botón Iniciar depuración en el depurador **estándar** barra de herramientas.  
  
 ![Ejecutar en el equipo Local](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 Si no ve el **estándar** barra de herramientas, haga clic en el **vista** menú, elija **las barras de herramientas**y, a continuación, haga clic en **estándar**.  
  
 La opción que seleccione en la lista desplegable permanece habilitada en el archivo de propiedades del proyecto y se convierte en el destino de ejecución predeterminado.  
  
 Además, puede establecer el destino de ejecución directamente en el archivo de propiedades del proyecto. Haga clic en el nombre del proyecto en **el Explorador de soluciones** y, a continuación, elija **propiedades**. Realice alguno de los siguientes procedimientos:  
  
-   En los proyectos de C# y Visual Basic, haga clic en **depurar** y, a continuación, seleccione **equipo Local** desde el **dispositivo de destino** lista desplegable.  
  
     ![C &#35; y la página de propiedades del proyecto de Visual Basic](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   En los proyectos de C++ y JavaScript, expanda la **propiedades de configuración** nodo, haga clic en **depuración**y, a continuación, seleccione **depurador Local de** desde el **depurador Para iniciar** lista.  
  
     ![C &#43; &#43; página de propiedades del proyecto de JavaScript](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  