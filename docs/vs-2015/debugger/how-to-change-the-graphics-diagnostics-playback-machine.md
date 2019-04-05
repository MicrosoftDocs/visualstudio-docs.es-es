---
title: Filtrar Cambiar la máquina de reproducción de diagnóstico de gráficos | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1f5f25bf9b0dc03afc7cb2ba334d85bd697b7dc5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994820"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Filtrar Cambio de la máquina de reproducción de Diagnóstico de gráficos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede reproducir información de gráficos mediante el uso de la máquina local, o mediante el uso de un dispositivo o equipo remoto.  
  
## <a name="choosing-a-playback-machine"></a>Elección de una máquina de reproducción  
 La máquina de reproducción es un equipo o dispositivo que se usa para reproducir eventos de gráficos desde un registro de gráficos. Normalmente, el equipo local es la opción más conveniente, pero no podría reproducir un problema de representación en un equipo que tenga un hardware diferente o las versiones del controlador que la máquina donde se capturó; Cuando esto sucede, puede elegir una máquina de reproducción remota que reproduce mejor el problema y seguir usando el equipo de desarrollo para diagnosticarlo.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Para utilizar el equipo local para reproducir información de gráficos  
  
1.  En la ventana de documento de registro de gráficos, elija el **máquina de reproducción** vínculo. El **conexiones del depurador remoto** aparece el cuadro de diálogo.  
  
2.  En **configuración Manual**, en el **dirección** propiedad, escriba `localhost`.  
  
3.  Establecer el **modo de autenticación** propiedad **ninguno**.  
  
4.  Elija el botón **Seleccionar**.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Para utilizar un equipo remoto para reproducir información de gráficos  
  
1.  En la ventana de documento de registro de gráficos, elija el **máquina de reproducción** vínculo. El **conexiones del depurador remoto** aparece el cuadro de diálogo.  
  
2.  En **configuración Manual**, en el **dirección** propiedad, escriba el nombre de dominio de Windows o la dirección IP del equipo o dispositivo que desea utilizar para reproducir información de gráficos.  
  
3.  Especifique el tipo de autorización que desea usar para proteger la conexión a la máquina de reproducción.  
  
    -   Para la autenticación de Windows, establezca el **modo de autenticación** propiedad **Windows**.  
  
    -   Sin autenticación, establezca el **modo de autenticación** propiedad **ninguno**.  
  
4.  Elija el botón **Seleccionar**.  
  
> [!NOTE]
>  El **conexiones del depurador remoto** cuadro de diálogo también podría mostrar destinos de depuración remota que están conectados directamente a la máquina de desarrollo o están en la misma subred. Puede usar uno de estos destinos de depuración remota como máquina de reproducción de diagnóstico de gráficos sin configurarlo manualmente. En el **conexiones del depurador remoto** cuadro de diálogo, seleccione el destino que desee y, a continuación, elija el **seleccione** botón.  
  
## <a name="see-also"></a>Vea también  
 [Documento de registro de gráficos](../debugger/graphics-log-document.md)
