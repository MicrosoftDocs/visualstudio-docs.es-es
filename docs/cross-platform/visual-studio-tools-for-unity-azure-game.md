---
title: Tutorial de Visual Studio Tools para juego de Unity Azure| Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: DA86FC7F-E456-4DFC-84BF-D780421508B9
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 204389c2341c3aa9f729b92b5f3d459e7b101d24
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2017
---
# <a name="test-the-sample-game"></a>Probar el juego de ejemplo

El juego de ejemplo es un juego de carreras sencillo que registra datos sobre el comportamiento del jugador y lo almacena en tablas fáciles de Azure. El juego de ejemplo también incluye escenas que leen los datos de Azure y los visualizan para el jugador.

En esta sección se explica de manera sencilla cómo jugar al juego de ejemplo y asegurarse de que funciona correctamente. En las secciones siguientes entraremos en más detalle explicando cómo funciona el juego de ejemplo.

## <a name="starting-the-game"></a>Iniciar el juego

1. En la ventana de proyecto de Unity, navegue a la carpeta **Assets/Azure Easy Tables sample game assets/Scenes**.

2. Haga doble clic en **MenuScene** para abrirlo.

3. En la ventana Unity Game, haga clic en el **menú desplegable de relación de aspecto** y elija **16:9**.

  ![Definir la relación de aspecto](media/vstu_azure-test-sample-game-image1.png)

4. Haga clic en el botón **Reproducir** para ejecutar el juego en el editor de Unity.


## <a name="complete-a-race"></a>Terminar una carrera

Antes de ver la tabla de clasificación o el mapa térmico, es mejor crear datos de ejemplo terminando la carrera al menos una vez.

1. Mientras se ejecuta el juego en el editor de Unity, haga clic en el botón **Race!** (Carrera) para empezar una nueva carrera.

2. Use **WASD** o las **teclas de dirección** para dirigir el coche y completar una vuelta a la pista en el sentido de las agujas del reloj. Para el ejemplo, asegúrese de chocarse contra algunas paredes del camino. Al depurar el resultado en la consola Unity se indicará si se ha registrado una colisión.

  >[!NOTE]
  > Si consigue que el coche se dé la vuelta y no puede continuar, haga clic en **Reiniciar**. Solo se envían datos a Azure al completarse una vuelta de la carrera.

  ![Empezar una carrera](media/vstu_azure-test-sample-game-image2.png)

3. Después de cruzar la línea de meta a cuadros, el juego debe mostrar un mensaje **Finalizado**. En este momento, los datos de choque se cargarán en Azure.

4. Si ha quedado entre los 10 más rápidos en completar la carrera, se le pedirá que escriba un nombre para mostrarlo en la puntuación más alta obtenida. Escriba su nombre y haga clic en **Enviar**.

  ![Empezar una carrera](media/vstu_azure-test-sample-game-image3.png)

## <a name="view-the-heatmap"></a>Ver el mapa térmico

1. Haga clic en el botón **View Crash Heatmap** (Ver mapa térmico de colisiones) de la escena de la carrera o seleccione **Crash Heatmap** (Mapa térmico de colisiones) en el menú principal.

2. La escena de mapa térmico carga datos de la tabla CrashInfo en Azure y muestra una esfera roja transparente en las ubicaciones donde los jugadores se han chocado contra las paredes de la pista de carreras. Si se producen varias colisiones en un área superpuesta, las esferas se mostrarán más brillantes.

  ![Mapa térmico](media/vstu_azure-test-sample-game-image4.png)

## <a name="view-the-leaderboard"></a>Ver la tabla de clasificación

1. Haga clic en el botón **Tabla de clasificación** desde la escena de la carrera o el menú principal.

2. La escena de tabla de clasificación carga los datos de puntuación alto de la tabla HighScoreInfo en Azure y muestra un nombre de jugador y un tiempo de vuelta para cada entrada de puntuación alta.

  ![Tabla de clasificación](media/vstu_azure-test-sample-game-image5.png)

## <a name="next-step"></a>Paso siguiente

* [Explicación de RaceScene](visual-studio-tools-for-unity-azure-racescene.md)
