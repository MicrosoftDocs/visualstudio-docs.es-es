---
title: "Informaci&#243;n general (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos definidos por el usuario"
  - "archivos .dbg"
  - "módulos"
  - "interfaces [Kit de desarrollo DIA (SDK)]"
  - "DBG (archivos)"
  - "procedimientos [Kit de desarrollo DIA (SDK)]"
  - "archivos ejecutables"
  - "Objetos COM, en el SDK de DIA"
  - "compilands"
  - "imágenes ejecutables"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Informaci&#243;n general (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilice el diámetro SDK para tener acceso a información de depuración de Microsoft.  El diámetro SDK proporciona API basado COM establecido que elimina la necesidad de escribir el código siempre que Microsoft cambie el formato de la información de depuración.  El diámetro SDK también permite leer de un conjunto seleccione de versiones anteriores de información de depuración, que se encuentran en los archivos .pdb y .dbg generados por versiones 5,0 de [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] y posterior.  
  
 Cada interfaz en el diámetro SDK representa un objeto COM, excepto si dicha de otra manera.  Las interfaces adicionales, por otros objetos, se crean mediante consultas explícitas, como [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), en lugar de llamar a `QueryInterface` en punteros existentes de la interfaz.  
  
## Vea también  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)