---
title: 'Tutorial de Azure para Visual Studio Tools para Unity: recursos de juego| Microsoft Docs'
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: C06FAB2E-F592-4EFF-B96A-58858C92DCEB
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- azure
- unity
ms.openlocfilehash: 19b98dc472b9e01529725b95133d289edff6334d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="import-sample-game-assets"></a>Importar los recursos de juego de muestra

Ahora que ha probado la funcionalidad básica y ha comprobado que funciona, es el momento de importar los recursos de juego de muestra.

## <a name="import-package"></a>Importar el paquete

1. Descargue el [paquete de recursos de juego de muestra](https://github.com/dantogno/UnityAzureSample/blob/master/Azure%20Easy%20tables%20sample%20game%20assets.unitypackage).

2. Asegúrese de que su proyecto de Unity está abierto y, luego, vaya a la ubicación de descarga y haga doble clic en el archivo. Se abrirá el cuadro de diálogo de importación de Unity.

3. Haga clic en **Todo** y en **Importar**. Espere a que se completen las barras de progreso resultantes.

  ![Importar el paquete](media/vstu_azure-import-sample-assets-image1.png)

## <a name="add-scenes-to-build-settings"></a>Agregar escenas a la configuración de compilación

Una vez que los archivos se hayan terminado de importar, deberá agregar los archivos de escena necesarios a la configuración de compilación del proyecto de Unity.

1. En la ventana del proyecto de Unity, navegue al directorio **Azure Easy Tables sample game assets/Scenes**.

2. En el menú de Unity, seleccione **Archivo > Configuración de compilación...** Se mostrará el cuadro de diálogo Configuración de compilación.

3. Arrastre los archivos **HeatmapScene**, **LeaderboardScene**, **MenuScene** y **RaceScene** desde la ventana del proyecto hasta la sección **Scenes In Build** (Escenas en compilación) del cuadro de diálogo Configuración de compilación.

  ![Importar el paquete](media/vstu_azure-import-sample-assets-image2.png)

4. En el menú de Unity, seleccione **Archivo > Guardar proyecto** para asegurarse de que se guarda la configuración de compilación.

## <a name="next-step"></a>Paso siguiente

* [Prueba de juegos de muestra](visual-studio-tools-for-unity-azure-game.md)