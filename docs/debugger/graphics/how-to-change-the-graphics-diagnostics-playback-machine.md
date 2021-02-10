---
title: Cambio de la máquina de reproducción de Diagnóstico de gráficos
description: Reproduzca información de gráficos desde un registro de gráficos mediante el equipo local o un equipo o dispositivo remoto que reproduzca mejor el problema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a0689238bf30947fa36ff58b969afa35a55003b5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889205"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Procedimiento para cambiar la máquina de reproducción de Diagnóstico de gráficos
Puede reproducir información de gráficos mediante el equipo local o un equipo o dispositivo remoto.

## <a name="choosing-a-playback-machine"></a>Elección de una máquina de reproducción
 La máquina de reproducción es la máquina o el dispositivo utilizados para reproducir eventos de gráficos desde un archivo de registro de gráficos. Normalmente, el equipo local es la opción más conveniente, pero es posible que un problema de representación no se reproduzca en un equipo que tenga versiones de hardware o de controlador diferentes de la máquina en la que se capturó. Cuando esto sucede, puede seleccionar una máquina de reproducción remota que reproduzca mejor el problema y seguir usando el equipo de desarrollo para diagnosticarlo.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Para usar el equipo local para reproducir la información de gráficos

1. En la ventana de documento de registro de gráficos, seleccione el vínculo **Máquina de reproducción**. Se mostrará el cuadro de diálogo **Conexiones del depurador remoto**.

2. En **Configuración manual**, en la propiedad **Dirección**, escriba `localhost`.

3. Establezca la propiedad **Modo de autenticación** en **Ninguno**.

4. Elija el botón **Seleccionar**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Para usar un equipo local para reproducir la información de gráficos

1. En la ventana de documento de registro de gráficos, seleccione el vínculo **Máquina de reproducción**. Se mostrará el cuadro de diálogo **Conexiones del depurador remoto**.

2. En **Configuración manual**, en la propiedad **Dirección**, escriba el nombre de dominio de Windows o la dirección IP del equipo o dispositivo que quiera usar para reproducir la información de gráficos.

3. Especifique el tipo de autorización que quiere usar para proteger la conexión a la máquina de reproducción.

    - Para la autenticación de Windows, establezca la propiedad **Modo de autenticación** en **Windows**.

    - En caso de que no haya autenticación, establezca la propiedad **Modo de autenticación** en **Ninguno**.

4. Elija el botón **Seleccionar**.

> [!NOTE]
> Es posible que en el cuadro de diálogo **Conexiones del depurador remoto** también se muestren destinos de depuración remota que están conectados directamente a su equipo de desarrollo o que se encuentran en la misma subred. Puede usar uno de estos destinos de depuración remota como máquina de reproducción de Diagnóstico de gráficos sin tener que aplicar la configuración manualmente. En el **cuadro de diálogo Conexiones del depurador remoto**, seleccione el destino que quiera y, a continuación, el botón **Seleccionar**.

## <a name="see-also"></a>Vea también
- [Documento de registro de gráficos](graphics-log-document.md)