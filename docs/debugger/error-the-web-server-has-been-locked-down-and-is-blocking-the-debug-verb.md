---
title: 'Error: El servidor Web se ha bloqueado y está bloqueando el verbo DEBUG | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_debug_verb_blocked
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2537868da6c72df9a68c492b650c72d8a980fcb
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474003"
---
# <a name="error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb"></a>Error: El servidor Web se ha bloqueado y está bloqueando el verbo DEBUG
No se pudo recorrer paso a paso por instrucciones una aplicación Web o un servicio Web XML porque se ha ejecutado la herramienta de cierre de IIS y se ha instalado y activado URLScan. Esta condición bloquea IIS para que no reciba el verbo DEBUG.  
  
 URLScan es una herramienta de seguridad que funciona junto con la Herramienta de cierre de IIS para ofrecer a los administradores de sitios Web IIS la capacidad de desactivar características innecesarias y restringir el tipo de solicitudes HTTP que puede procesar el servidor. Al bloquear solicitudes HTTP específicas, la herramienta de seguridad URLScan evita que solicitudes potencialmente nocivas lleguen al servidor y produzcan daños.  
  
 Si la aplicación se ejecuta en IIS 6.0 en Windows Server 2003, no es preciso ejecutar la herramienta de bloqueo de IIS porque IIS 6.0 proporciona la misma funcionalidad.  
  
### <a name="to-enable-debugging-on-a-web-server-with-urlscan-installed"></a>Para habilitar la depuración en un servidor Web con URLScan instalado  
  
1.  Busque el archivo Urlscan.ini. En general se encontrará en un directorio parecido al siguiente:  
  
     C:\WINNT\System32\Inetsrv\urlscan  
  
2.  Crear una copia del archivo y asígnele el nombre **Urlscan.old**.  
  
3.  Abra la copia original del archivo Urlscan.ini en el Bloc de notas o el editor de texto que prefiera.  
  
4.  En Urlscan.ini, busque la sección [AllowVerbs]. Agregue DEBUG a la sección [AllowVerbs]. Si ve ;DEBUG en la sección [AllowVerbs], quite el punto y coma para no marcar el verbo como comentario.  
  
5.  Busque la sección [DenyVerbs]. Si aparece DEBUG en la sección [DenyVerbs], quítelo.  
  
6.  Guarde el archivo.  
  
7.  Reinicie el servidor o reinicie IIS.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de aplicaciones Web: Errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Error: El servidor web no pudo encontrar el recurso solicitado](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)