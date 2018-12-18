---
title: Recopilar datos de interacción de capas | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.tierinteraction
helpviewer_keywords:
- Profiling Tools,ADO.NET profiling
- tier interaction profiling method
- Profiling Tools,tier-interaction method
- ADO.NET performance profiling
ms.assetid: 47a944c2-3098-497c-8fc7-e1f43d750bbc
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31e2d46992b48b987966bac7d7dc68787f4016c2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761186"
---
# <a name="collecting-tier-interaction-data"></a>Recopilar datos de interacción de capas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La generación de perfiles de interacción de capas proporciona información adicional sobre los tiempos de ejecución de funciones de aplicaciones de varias capas que se comunican con las bases de datos a través de servicios de ADO.NET. Los datos se recopilan solamente para las llamadas a funciones sincrónicas.  
  
 **Ediciones de Visual Studio**  
  
 Los datos de generación de perfiles de interacción de capas se pueden recopilar usando Visual Studio Ultimate, Visual Studio Premium o Visual Studio Professional. Sin embargo, los datos de generación de perfiles de interacción de capas solo se pueden ver en VS Ultimate y VS Premium.  
  
 **Windows 8 y Windows Server 2012**  
  
 Para recopilar datos de interacción de capas de aplicaciones de escritorio de Windows 8 o aplicaciones de Windows Server 2012, debe usar el método de instrumentación. No se pueden recopilar datos de interacción de capas para las aplicaciones de la Tienda Windows. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md). Puede incluir datos de interacción de capas en todos los métodos de generación de perfiles de otras versiones compatibles de Windows.  
  
 **Asistente de rendimiento**  
  
 Debido a un error en el Asistente para rendimiento, debe agregar la opción de recopilación de datos de interacción de capas a una ejecución de generación de perfiles desde el Explorador de rendimiento. También debe agregar el proyecto, el archivo ejecutable o el sitio web al nodo de destino del Explorador de rendimiento.  
  
### <a name="to-add-tier-interaction-data-to-a-profiling-run-by-using-the-performance-session-property-pages"></a>Para agregar datos de interacción de capas a una ejecución de generación de perfiles utilizando las páginas de propiedades de la sesión de rendimiento  
  
1.  En el Explorador de rendimiento, elija **Propiedades** en el menú contextual.  
  
2.  Seleccione la página **Interacciones de capas** y, a continuación, active la casilla **Habilitar la generación de perfiles de interacción de capas**.  
  
3.  En el Explorador de rendimiento, seleccione el nodo **Destinos** y, después, especifique el proyecto, el archivo ejecutable o el sitio web cuyo perfil desea generar.  
  
## <a name="see-also"></a>Vea también  
 [Vista Interacciones de capas](../profiling/tier-interactions-view.md)



