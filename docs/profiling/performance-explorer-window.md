---
title: Ventana Explorador de rendimiento | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 16b3c7111ddda71d070456c409b95f53c04f0063
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/21/2018
---
# <a name="performance-explorer-window"></a>Ventana Explorador de rendimiento

La ventana **Explorador de rendimiento** del IDE de Visual Studio le permite configurar e iniciar sesiones de rendimiento mediante las Herramientas de generación de perfiles de Visual Studio.

## <a name="performance-explorer-toolbar"></a>Barra de herramientas de Explorador de rendimiento

Las siguientes opciones están disponibles en la barra **Herramientas de rendimiento**:

- **Iniciar Asistente de rendimiento**: muestra el Asistente de rendimiento para agregar una nueva sesión de rendimiento a la ventana Explorador de rendimiento.

- **Nueva sesión de rendimiento**: agrega una sesión de rendimiento vacía a la ventana Explorador de rendimiento.

- **Iniciar**: la lista de botones de comando **Iniciar** le permite iniciar la aplicación de destino que tiene la generación de perfiles habilitada (**Iniciar con la generación de perfiles**) o suspendida (**Inicio con la generación de perfiles en pausa**).

- **Método**: especifica si el método de generación de perfiles de la sesión es de muestreo o de instrumentación.

- **Detener**: sale inmediatamente de la aplicación de destino y el generador de perfiles.

- **Adjuntar y separar**: muestra el cuadro de diálogo **Adjuntar el generador de perfiles al proceso** para seleccionar un proceso en ejecución al que se va a adjuntar el generador de perfiles.

## <a name="performance-explorer-window"></a>Ventana Explorador de rendimiento

La ventana **Explorador de rendimiento** contiene un control de árbol que muestra los archivos binarios y los archivos de datos de informe de una o varias sesiones de rendimiento.

- **Nombre de la sesión**: la raíz del control de árbol contiene el nombre de la sesión. Haga clic con el botón derecho en el nombre de sesión para establecer las propiedades de la sesión o para iniciar la aplicación de destino y el generador de perfiles.

- **Destinos**: muestra los nombres de los archivos binarios de los que se van a generar perfiles en la sesión. Haga clic con el botón derecho en **Destinos** para agregar o quitar un archivo binario, proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o sitio web. Haga clic con el botón derecho en un nombre de destino para establecer las propiedades del binario individual.

- **Informes**: muestra los nombres de archivos de datos del generador de perfiles que se generan para la sesión. Haga clic con el botón derecho en **Informes** para agregar un informe existente o comparar dos archivos de datos del generador de perfiles. Haga clic con el botón derecho en un nombre de informe para abrir, quitar o exportar un archivo de datos del generador de perfiles.

## <a name="see-also"></a>Vea también

[Información general](../profiling/overviews-performance-tools.md)  
[Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)  
[Controlar la recopilación de datos](../profiling/controlling-data-collection.md)