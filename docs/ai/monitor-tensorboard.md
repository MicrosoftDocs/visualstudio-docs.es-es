---
title: Supervisión con TensorBoard
description: Aprenda a usar Visual Studio para visualizar el progreso del entrenamiento del modelo con TensorBoard.
ms.custom: SEO-VS-2020
author: jillre
ms.author: jillfra
manager: jmartens
monikerRange: vs-2017
ms.date: 11/13/2017
ms.topic: how-to
ms.workload:
- multiple
ms.openlocfilehash: edb6fe17902ad84ec6d7a6e5b9929bd965e7c29b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99841398"
---
# <a name="monitor-with-tensorboard"></a>Supervisión con TensorBoard

Puede visualizar el progreso del entrenamiento del modelo con TensorBoard.

1. Haga clic con el botón derecho en el proyecto, haga clic en **Ejecutar TensorBoard** y, después, seleccione el directorio de los registros de TensorBoard de salida.

    ![Captura de pantalla del Explorador de soluciones de Visual Studio con el proyecto MNIST seleccionado. Se muestra un menú contextual abierto con el comando Run TensorBoard (Ejecutar TensorBoard) seleccionado.](media/monitor-tensorboard/run-tensorboard.png)

2. Observe que el error disminuye con el tiempo, lo que significa que la calidad está mejorando.

    ![Captura de pantalla de la ventana principal de TensorBoard, en la que se muestran visualizaciones gráficas de los datos de los registros de TensorBoard.](media/monitor-tensorboard/tensorboard.png)
