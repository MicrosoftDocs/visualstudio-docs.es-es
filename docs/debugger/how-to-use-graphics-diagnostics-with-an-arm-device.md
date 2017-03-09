---
title: "C&#243;mo: Usar diagn&#243;sticos de gr&#225;ficos con un dispositivo ARM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Usar diagn&#243;sticos de gr&#225;ficos con un dispositivo ARM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El Diagnóstico de Gráficos es compatible con la depuración remota de las aplicaciones Direct3D en dispositivos basados en ARM que se ejecuten en Windows RT 8.1 o Windows Phone 8.1.  Puede capturar información de gráficos de la aplicación Direct3D mientras se ejecuta en el dispositivo o utilizar el dispositivo como máquina de reproducción para información de gráficos capturada previamente.  
  
## Uso del Diagnóstico de gráficos con un dispositivo basado en ARM  
 Como Visual Studio no se puede ejecutar en dispositivos basados en ARM, debe utilizar el depurador remoto para analizar una aplicación que se ejecuta en ellos.  El depurador remoto es compatible con la captura de gráficos y la reproducción, de modo que puede diagnosticar errores de presentación y evaluar el rendimiento de los gráficos en estos dispositivos de una manera tan sencilla como puede depurar la aplicación en ellos.  
  
 Para utilizar las funciones del diagnóstico de gráficos, primero habilite la depuración remota en el dispositivo.  
  
#### Habilitación de la depuración remota en el dispositivo basado en ARM  
  
1.  Instale la [directiva ARM Kits](http://msdn.microsoft.com/windows/desktop/dn469188) en el dispositivo basado en ARM.  
  
2.  Instale las [herramientas de depuración remota](http://go.microsoft.com/fwlink/?LinkId=393086) en el dispositivo basado en ARM.  
  
> [!IMPORTANT]
>  Para los dispositivos Windows Phone 8.1, es posible que tenga que registrar el teléfono durante el desarrollo.  Para ello, debe ser un desarrollador registrado.  Para obtener más información, vea [Cómo implementar y ejecutar una aplicación para Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Después de habilitar la depuración remota en el dispositivo, conviértalo en su destino de depuración e inicie el Diagnóstico de gráficos.  
  
#### Configuración e inicio de Diagnóstico de gráficos en su dispositivo  
  
1.  En la lista desplegable **Plataformas de solución**, seleccione **ARM** para que su dispositivo basado en ARM esté disponible como objetivo de depuración remoto.  
  
2.  En la lista desplegable **Depurar destino**, seleccione su dispositivo basado en ARM.  
  
3.  En el menú, elija **Depurar**, **Gráficos**, **Iniciar diagnóstico**.  \(Teclado: Alt\+F5\)  
  
## Vea también  
 [Ejecutar aplicaciones de la Tienda Windows en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Cómo: Cambiar la máquina de reproducción de diagnósticos de gráficos](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)