---
title: Vista Módulos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.modules
helpviewer_keywords:
- Modules view
- profiling tools reports, Modules view
- profiling tools, Modules view
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fcafc9960f9ff4c053e63b1fc5abfd75bb41c995
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2018
ms.locfileid: "35254581"
---
# <a name="modules-view"></a>Vista Módulos
En la vista Módulos se enumeran los módulos de los datos de generación de perfiles. Cada módulo es el nodo raíz de un árbol jerárquico. Las funciones del módulo para las que se generan perfiles se enumeran debajo del nodo de módulo. Si los datos de generación de perfiles se han recopilado mediante el método de muestreo, la información de la línea se enumera debajo del nodo de función y los datos del puntero de instrucción se muestran debajo del nodo de línea.  
  
 Expanda o contraiga el nombre del módulo para mostrar o cerrar la vista de los datos de rendimiento del módulo.  
  
 Para agregar o quitar columnas, haga clic con el botón derecho en la ventana del informe y, a continuación, seleccione **Agregar o quitar columnas**. Puede ordenar los datos si hace clic en el nombre de una columna. Para obtener más información, vea [Cómo: Personalizar una pestaña integrada](../profiling/how-to-customize-report-view-columns.md).  
  
 Las columnas que están disponibles en la vista Módulos dependen del método de generación de perfiles (muestreo o instrumentación) usado para recopilar los datos y de si los datos de memoria de .NET se han recopilado en la ejecución de generación de perfiles.  
  
## <a name="see-also"></a>Vea también  
 [Vista Módulos](../profiling/modules-view-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-instrumentation-data.md)   
 [Vista Módulos: instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista Módulos: muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-contention-data.md)