---
title: 'Error: el servidor Web no encontró el recurso solicitado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 555bb56ee84b7bc48f6b6453c11daef366f97e49
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2020
ms.locfileid: "75845116"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Error: El servidor Web no pudo encontrar el recurso solicitado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por motivos de seguridad, IIS ha devuelto un error genérico.  
  
 Una posible causa es la configuración de seguridad del servidor. IIS 6.0 y las versiones anteriores utilizaban un programa complementario, denominado URLScan, para filtrar solicitudes sospechosas y con formato incorrecto. IIS 7.0 dispone de Filtrado de solicitudes integrado para el mismo propósito. En ambos casos, un filtrado de solicitudes demasiado restrictivo puede impedir que Visual Studio depure el servidor.  
  
 Existen muchas posibles causas de este error. Entre las causas más comunes se incluyen un problema con la instalación o la configuración de IIS, la configuración del sitio web o los permisos del sistema de archivos. Puede intentar obtener acceso al recurso mediante un explorador. Según cómo esté configurado IIS, podría tener que utilizar un explorador local en el servidor o examinar el registro de errores de IIS para obtener un mensaje de error detallado.  
  
 Para obtener más información acerca de cómo solucionar problemas de IIS, vea [Gestión y administración de IIS](https://www.iis.net/learn/manage/provisioning-and-managing-iis/iis-management-and-administration).  
  
## <a name="see-also"></a>Vea también  
 [Herramienta de seguridad UrlScan](/iis/extensions/working-with-urlscan/urlscan-3-reference)   
 [Error: El servidor web se ha bloqueado y está impidiendo la ejecución del verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)
