---
title: 'Cómo: cambiar la máquina de reproducción de Diagnóstico de gráficos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a41caf3f866c4a21d0a44fc69932066b2b7d923
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72735060"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Cómo: Cambiar la máquina de reproducción de diagnósticos de gráficos
Puede reproducir información de gráficos mediante el equipo local o mediante un equipo o dispositivo remoto.

## <a name="choosing-a-playback-machine"></a>Elección de una máquina de reproducción
 El equipo de reproducción es un equipo o dispositivo que se usa para reproducir eventos de gráficos desde un registro de gráficos. Normalmente, el equipo local es la opción más conveniente, pero es posible que un problema de representación no se reproduzca en un equipo que tiene versiones de hardware o de controlador diferentes de la máquina en la que se capturó. Cuando esto sucede, puede elegir una máquina de reproducción remota que reproduzca mejor el problema y seguir usando el equipo de desarrollo para diagnosticarlo.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Para usar el equipo local para reproducir la información de gráficos

1. En la ventana de documento de registro de gráficos, elija el vínculo **máquina de reproducción** . Aparece el cuadro de diálogo **conexiones del Depurador remoto** .

2. En **configuración manual**, en la propiedad **dirección** , escriba `localhost`.

3. Establezca la propiedad **modo de autenticación** en **ninguno**.

4. Elija el botón **Seleccionar**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Para usar un equipo remoto para reproducir información de gráficos

1. En la ventana de documento de registro de gráficos, elija el vínculo **máquina de reproducción** . Aparece el cuadro de diálogo **conexiones del Depurador remoto** .

2. En **configuración manual**, en la propiedad **Dirección** , escriba el nombre de dominio de Windows o la dirección IP del equipo o dispositivo que desea usar para reproducir la información de gráficos.

3. Especifique el tipo de autorización que desea usar para proteger la conexión a la máquina de reproducción.

    - Para la autenticación de Windows, establezca la propiedad **modo de autenticación** en **Windows**.

    - Para sin autenticación, establezca la propiedad **modo de autenticación** en **ninguno**.

4. Elija el botón **Seleccionar**.

> [!NOTE]
> El cuadro de diálogo **conexiones del Depurador remoto** también podría mostrar destinos de depuración remota que están conectados directamente a su equipo de desarrollo o que se encuentran en la misma subred. Puede usar uno de estos destinos de depuración remota como Diagnóstico de gráficos máquina de reproducción sin configurarlo manualmente. En el cuadro de diálogo **conexiones del Depurador remoto** , seleccione el destino que desee y, a continuación, elija el botón **seleccionar** .

## <a name="see-also"></a>Vea también
- [Documento de registro de gráficos](graphics-log-document.md)