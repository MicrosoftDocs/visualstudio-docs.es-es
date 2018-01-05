---
title: "Introducción (Debug Interface Access SDK) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d37843917be3a2668e9a2887f046eaee00600dc8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introducción (Debug Interface Access SDK)
El Debug Interface Access (DIA) SDK proporciona documentación de instrucciones y un ejemplo que muestra cómo utilizar la API de DIA. Use las interfaces y métodos en el SDK de DIA para desarrollar aplicaciones personalizadas que abra los archivos .pdb y .dbg y buscar símbolos, valores, atributos, direcciones y otra información de depuración en su contenido. Este SDK proporciona también las tablas de referencia para las propiedades asociadas a los símbolos encontrados en aplicaciones de C++.  
  
 Para utilizar mejor el SDK de DIA, debe estar familiarizado con lo siguiente:  
  
-   Lenguaje de programación de C++  
  
-   Programación de COM  
  
-   Entorno de desarrollo integrado de Visual Studio (IDE) para compilar los ejemplos  
  
 El SDK de DIA normalmente se instala con Visual Studio y su ubicación predeterminada es *[unidad]*\Program 9.0\DIA de Visual Studio SDK. Como parte de la instalación, el msdia90.dll, que implementa el SDK de DIA, se registra automáticamente por lo que todo lo que debe hacer para que la use incluir `dia2.h` en su programa y vincularlo a `diaguids.lib`.  
  
 Encabezado: include\dia2.h  
  
 Biblioteca: lib\diaguids.lib  
  
 DLL: bin\msdia80.dll  
  
 IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Revisa la arquitectura básica de diámetro  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones paso a paso sobre cómo usar la API de DIA para consultar un archivo .pdb.  
  
## <a name="see-also"></a>Vea también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)