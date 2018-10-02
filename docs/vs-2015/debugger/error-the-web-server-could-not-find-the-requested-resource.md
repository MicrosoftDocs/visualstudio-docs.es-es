---
title: 'Error: El servidor Web no pudo encontrar el recurso solicitado | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc41673da6157306cd0e4e66070717d5745d6218
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47567045"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Error: El servidor Web no pudo encontrar el recurso solicitado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Error: el servidor Web no pudo encontrar el recurso solicitado](https://docs.microsoft.com/visualstudio/debugger/error-the-web-server-could-not-find-the-requested-resource).  
  
Por motivos de seguridad, IIS ha devuelto un error genérico.  
  
 Una posible causa es la configuración de seguridad del servidor. IIS 6.0 y las versiones anteriores utilizaban un programa complementario, denominado URLScan, para filtrar solicitudes sospechosas y con formato incorrecto. IIS 7.0 dispone de Filtrado de solicitudes integrado para el mismo propósito. En ambos casos, un filtrado de solicitudes demasiado restrictivo puede impedir que Visual Studio depure el servidor.  
  
 Existen muchas posibles causas de este error. Entre las causas más comunes se incluyen un problema con la instalación o la configuración de IIS, la configuración del sitio web o los permisos del sistema de archivos. Puede intentar obtener acceso al recurso mediante un explorador. Según cómo esté configurado IIS, podría tener que utilizar un explorador local en el servidor o examinar el registro de errores de IIS para obtener un mensaje de error detallado.  
  
 Para obtener más información sobre cómo solucionar problemas de IIS, consulte [IIS de administración](http://go.microsoft.com/fwlink/?LinkId=255872).  
  
## <a name="see-also"></a>Vea también  
 [Herramienta de seguridad UrlScan](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [Error: El servidor web se ha bloqueado y está impidiendo la ejecución del verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)



