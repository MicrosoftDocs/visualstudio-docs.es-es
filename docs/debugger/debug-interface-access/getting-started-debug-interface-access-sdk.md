---
title: "Introducci&#243;n (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos .dbg"
  - "DBG (archivos)"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Introducci&#243;n (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Fuentes de Access SDK \(DIA\) de la interfaz de depuración a la documentación educacional y un ejemplo que muestra cómo utilizar el diámetro API.  Utilice las interfaces y los métodos del diámetro SDK para desarrollar aplicaciones personalizadas que abra los archivos .pdb y .dbg y buscan el contenido de los símbolos, los valores, los atributos, las direcciones, y otra información de depuración.  Este SDK también proporciona tablas de referencia para las propiedades asociadas con símbolos situados en las aplicaciones de C\+\+.  
  
 Al usar mejor el diámetro SDK, debe estar familiarizado con el siguiente:  
  
-   lenguaje de programación de C\+\+  
  
-   programación COM  
  
-   entorno de desarrollo integrado de Visual Studio \(IDE\) para compilar los ejemplos  
  
 El diámetro SDK está normalmente instalado con Visual Studio y su ubicación predeterminada es *\[\] unidad*\\Program Files\\Microsoft Visual Studio 9.0\\DIA SDK.  Como parte de la instalación, el msdia90.dll, que implementa el diámetro SDK, se registra automáticamente en todo lo que necesita hacer para utilizar que es incluir `dia2.h` en el programa y el vínculo a `diaguids.lib`.  
  
 encabezado: incluyen \\ dia2.h  
  
 biblioteca: lib \\ diaguids.lib  
  
 DLL: bin \\ msdia80.dll  
  
 IDL: IDL \\ dia2.idl  
  
## En esta sección  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Revisar la arquitectura básica del diámetro.  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones paso a paso sobre cómo utilizar el diámetro API para ver un archivo .pdb.  
  
## Vea también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)