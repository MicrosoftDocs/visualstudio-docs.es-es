---
title: 'Cómo: cambiar la máquina de reproducción de diagnóstico de gráficos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 143ae65b8d7db584546c250bf5d032450bf220aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473876"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Cómo: Cambiar la máquina de reproducción de diagnóstico de gráficos
Puede reproducir información de gráficos mediante el equipo local, o mediante el uso de un equipo o dispositivo remoto.  
  
## <a name="choosing-a-playback-machine"></a>Elegir una máquina de reproducción  
 La máquina de reproducción es un equipo o dispositivo que se usa para reproducir eventos de gráficos desde un registro de gráficos. Normalmente, el equipo local es la opción más conveniente, pero no puede reproducir un problema de representación en un equipo que tenga un hardware diferente o versiones del controlador de la máquina donde se capturaron; Cuando esto ocurre, puede elegir una máquina de reproducción remota que mejor se reproduzca el problema y seguir usando el equipo de desarrollo para diagnosticarlo.  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Para usar el equipo local para reproducir información de gráficos  
  
1.  En la ventana de documento de registro de gráficos, elija la **máquina de reproducción** vínculo. El **conexiones del depurador remoto** aparece el cuadro de diálogo.  
  
2.  En **configuración Manual**, en la **dirección** propiedad, escriba `localhost`.  
  
3.  Establecer el **modo de autenticación** propiedad **ninguno**.  
  
4.  Elija la **seleccione** botón.  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Para usar un equipo remoto para reproducir información de gráficos  
  
1.  En la ventana de documento de registro de gráficos, elija la **máquina de reproducción** vínculo. El **conexiones del depurador remoto** aparece el cuadro de diálogo.  
  
2.  En **configuración Manual**, en la **dirección** propiedad, escriba el nombre de dominio de Windows o la dirección IP de la máquina o dispositivo que desee usar para reproducir información de gráficos.  
  
3.  Especifique el tipo de autorización que desea usar para proteger la conexión a la máquina de reproducción.  
  
    -   Para la autenticación de Windows, establecer el **modo de autenticación** propiedad **Windows**.  
  
    -   Si no desea autenticación, establezca el **modo de autenticación** propiedad **ninguno**.  
  
4.  Elija la **seleccione** botón.  
  
> [!NOTE]
>  El **conexiones del depurador remoto** cuadro de diálogo puede aparecer también destinos de depuración remotos que están conectados directamente a su equipo de desarrollo o en la misma subred. Puede usar uno de estos destinos de depuración remotos como la máquina de reproducción de diagnóstico de gráficos sin configurarla manualmente. En el **conexiones del depurador remoto** cuadro de diálogo, seleccione el destino que desee y, a continuación, elija la **seleccione** botón.  
  
## <a name="see-also"></a>Vea también  
 [Documento de registro de gráficos](graphics-log-document.md)