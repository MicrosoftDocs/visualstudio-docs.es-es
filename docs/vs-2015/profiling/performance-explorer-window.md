---
title: Ventana Explorador de rendimiento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performanceexplorer
- vs.performance.explorer
helpviewer_keywords:
- performance tools, Performance Explorer
ms.assetid: cb6a6efc-93a5-49a2-8d03-6969b5f3b6d7
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a370ae802408ecc821de4cd15824f9d1fca42b75
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105336"
---
# <a name="performance-explorer-window"></a>Ventana Explorador de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La ventana **Explorador de rendimiento** del entorno de desarrollo integrado (IDE) de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] le permite configurar e iniciar sesiones de rendimiento mediante las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
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
  
- **Destinos**: muestra los nombres de los archivos binarios de los que se van a generar perfiles en la sesión. Haga clic con el botón derecho en **Destinos** para agregar o quitar un archivo binario, proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o sitio web. Haga clic con el botón derecho en un nombre de destino para establecer las propiedades del binario individual.  
  
- **Informes**: muestra los nombres de archivos de datos del generador de perfiles que se generan para la sesión. Haga clic con el botón derecho en **Informes** para agregar un informe existente o comparar dos archivos de datos del generador de perfiles. Haga clic con el botón derecho en un nombre de informe para abrir, quitar o exportar un archivo de datos del generador de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)
