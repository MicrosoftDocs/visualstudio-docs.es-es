---
title: 'Error: El servidor Web no pudo encontrar el recurso solicitado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c0b37e96db46a43b869867b8b5e37f857e75aff9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850282"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>Error: El servidor web no pudo encontrar el recurso solicitado
Por motivos de seguridad, IIS ha devuelto un error genérico.

Una posible causa es la configuración de seguridad del servidor. IIS 6.0 y las versiones anteriores utilizaban un programa complementario, denominado URLScan, para filtrar solicitudes sospechosas y con formato incorrecto. IIS 7.0 dispone de Filtrado de solicitudes integrado para el mismo propósito. En ambos casos, un filtrado de solicitudes demasiado restrictivo puede impedir que Visual Studio depure el servidor.

Otra causa posible de este error es que no se ha iniciado el servicio W3SVC de IIS. Compruebe que este servicio está iniciado (gris) en la ventana Servicios (*services.msc*).

Hay numerosas otras causas posibles de este error. Entre las causas más comunes se incluyen un problema con la instalación o la configuración de IIS, la configuración del sitio web o los permisos del sistema de archivos. Puede intentar obtener acceso al recurso mediante un explorador. Según cómo esté configurado IIS, podría tener que utilizar un explorador local en el servidor o examinar el registro de errores de IIS para obtener un mensaje de error detallado.

 Para obtener más información acerca de cómo solucionar problemas de IIS, vea [Gestión y administración de IIS](/iis/manage/provisioning-and-managing-iis/iis-management-and-administration).

## <a name="see-also"></a>Vea también
- [Error: El servidor web se ha bloqueado y está impidiendo la ejecución del verbo DEBUG](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)