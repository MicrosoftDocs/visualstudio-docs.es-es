---
title: Recopilar datos de interacción de capas | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fcdab1fcb776a729d00a143dfc318053b74c5cf5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831507"
---
# <a name="collect-tier-interaction-data"></a>Recopilar datos de interacción de capas

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de funciones de aplicaciones de varias capas que se comunican con las bases de datos a través de servicios de ADO.NET. Los datos se recopilan solamente para las llamadas a funciones sincrónicas.

**Ediciones de Visual Studio**

Los datos de generación de perfiles de interacción de capas se pueden recopilar con cualquier edición de Visual Studio. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en Visual Studio Enterprise.

**Windows 8 y Windows Server 2012**

Para recopilar datos de interacción de capas de aplicaciones de escritorio de Windows 8 o aplicaciones de Windows Server 2012, debe usar el método de instrumentación. No se pueden recopilar datos de interacción de capas para las aplicaciones para UWP. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Puede incluir datos de interacción de capas en todos los métodos de generación de perfiles de otras versiones compatibles de Windows.

**Asistente de rendimiento**

Debido a un error en el Asistente para rendimiento, debe agregar la opción de recopilación de datos de interacción de capas a una ejecución de generación de perfiles desde el Explorador de rendimiento. También debe agregar el proyecto, el archivo ejecutable o el sitio web al nodo de destino del Explorador de rendimiento.

## <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Para agregar datos de interacción de capas a una ejecución de generación de perfiles utilizando las páginas de propiedades de la sesión de rendimiento

1. En el Explorador de rendimiento, elija **Propiedades** en el menú contextual.

2. Seleccione la página **Interacciones de capas** y, a continuación, active la casilla **Habilitar la generación de perfiles de interacción de capas**.

3. En el Explorador de rendimiento, seleccione el nodo **Destinos** y, después, especifique el proyecto, el archivo ejecutable o el sitio web cuyo perfil desea generar.

## <a name="see-also"></a>Vea también

[Interacciones de capas (vista)](../profiling/tier-interactions-view.md)