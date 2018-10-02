---
title: 'Cómo: usar diagnóstico de gráficos con un dispositivo ARM | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 24067412f875001185a0709c41f930ce3cdc8f3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578478"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Cómo: Usar diagnóstico de gráficos con un dispositivo ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: usar diagnóstico de gráficos con un dispositivo ARM](https://docs.microsoft.com/visualstudio/debugger/graphics/how-to-use-graphics-diagnostics-with-an-arm-device).  
  
El Diagnóstico de Gráficos es compatible con la depuración remota de las aplicaciones Direct3D en dispositivos basados en ARM que se ejecuten en Windows RT 8.1 o Windows Phone 8.1. Puede capturar información de gráficos de la aplicación Direct3D mientras se ejecuta en el dispositivo o utilizar el dispositivo como máquina de reproducción para información de gráficos capturada previamente.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Uso del Diagnóstico de gráficos con un dispositivo basado en ARM  
 Como Visual Studio no se puede ejecutar en dispositivos basados en ARM, debe utilizar el depurador remoto para analizar una aplicación que se ejecuta en ellos. El depurador remoto es compatible con la captura de gráficos y la reproducción, de modo que puede diagnosticar errores de presentación y evaluar el rendimiento de los gráficos en estos dispositivos de una manera tan sencilla como puede depurar la aplicación en ellos.  
  
 Para utilizar las funciones del diagnóstico de gráficos, primero habilite la depuración remota en el dispositivo.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Habilitación de la depuración remota en el dispositivo basado en ARM  
  
1.  Instalar el [ARM Kits directiva](http://msdn.microsoft.com/windows/desktop/dn469188) en su dispositivo basado en ARM.  
  
2.  Instalar el [herramientas de depuración remota](http://go.microsoft.com/fwlink/?LinkId=393086) en su dispositivo basado en ARM.  
  
> [!IMPORTANT]
>  Para los dispositivos Windows Phone 8.1, es posible que tenga que registrar el teléfono durante el desarrollo. Para ello, debe ser un desarrollador registrado. Para obtener más información, consulte [cómo implementar y ejecutar una aplicación para Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Después de habilitar la depuración remota en el dispositivo, conviértalo en su destino de depuración e inicie el Diagnóstico de gráficos.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Configuración e inicio de Diagnóstico de gráficos en su dispositivo  
  
1.  En el **plataformas de solución** lista desplegable, seleccione **ARM** para que el dispositivo basado en ARM estará disponible como un destino de depuración remoto.  
  
2.  En el **depurar destino** lista desplegable, seleccione el dispositivo ARM.  
  
3.  En el menú, elija **depurar**, **gráficos**, **Iniciar diagnóstico**. (Teclado: Alt+F5)  
  
## <a name="see-also"></a>Vea también  
 [Ejecutar Windows Store apps en un equipo remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Cómo: Cambiar la máquina de reproducción de diagnóstico de gráficos](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)



