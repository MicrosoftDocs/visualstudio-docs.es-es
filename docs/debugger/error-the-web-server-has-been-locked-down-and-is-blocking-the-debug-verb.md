---
title: "Error: El servidor Web se ha bloqueado y est&#225; bloqueando el verbo DEBUG | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.webdbg_debug_verb_blocked"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "depurador, errores de aplicación Web"
ms.assetid: 9c8c4812-17db-484d-9c1b-ffd9e3bfef5a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Error: El servidor Web se ha bloqueado y est&#225; bloqueando el verbo DEBUG
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

No se pudo recorrer paso a paso por instrucciones una aplicación Web o un servicio Web XML porque se ha ejecutado la herramienta de cierre de IIS y se ha instalado y activado URLScan.  Esta condición bloquea IIS para que no reciba el verbo DEBUG.  
  
 URLScan es una herramienta de seguridad que funciona junto con la Herramienta de cierre de IIS para ofrecer a los administradores de sitios Web IIS la capacidad de desactivar características innecesarias y restringir el tipo de solicitudes HTTP que puede procesar el servidor.  Al bloquear solicitudes HTTP específicas, la herramienta de seguridad URLScan evita que solicitudes potencialmente nocivas lleguen al servidor y produzcan daños.  
  
 Si la aplicación se ejecuta en IIS 6.0 en Windows Server 2003, no es preciso ejecutar la herramienta de bloqueo de IIS porque IIS 6.0 proporciona la misma funcionalidad.  
  
### Para habilitar la depuración en un servidor Web con URLScan instalado  
  
1.  Busque el archivo Urlscan.ini.  En general se encontrará en un directorio parecido al siguiente:  
  
     C:\\WINNT\\System32\\Inetsrv\\urlscan  
  
2.  Cree una copia del archivo y asígnele el nombre Urlscan.old.  
  
3.  Abra la copia original del archivo Urlscan.ini en el Bloc de notas o el editor de texto que prefiera.  
  
4.  En Urlscan.ini, busque la sección \[AllowVerbs\].  Agregue DEBUG a la sección \[AllowVerbs\].  Si ve ;DEBUG en la sección \[AllowVerbs\], quite el punto y coma para no marcar el verbo como comentario.  
  
5.  Busque la sección \[DenyVerbs\].  Si aparece DEBUG en la sección \[DenyVerbs\], quítelo.  
  
6.  Guarde el archivo.  
  
7.  Reinicie el servidor o reinicie IIS.  
  
## Vea también  
 [Depurar las aplicaciones Web: errores y solución de problemas](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Error: El servidor Web no pudo encontrar el recurso solicitado](../debugger/error-the-web-server-could-not-find-the-requested-resource.md)