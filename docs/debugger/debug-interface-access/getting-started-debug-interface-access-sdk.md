---
title: Introducción (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24dc53efe0b7e30d2b585519d0ca0a8c070791d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031209"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introducción (Debug Interface Access SDK)
El Debug Interface Access (DIA) SDK proporciona documentación con instrucciones y un ejemplo que ilustra cómo usar la API de DIA. Use las interfaces y métodos en el SDK de DIA para desarrollar aplicaciones personalizadas que abrir los archivos .pdb y .dbg y buscar su contenido para los símbolos, valores, atributos, las direcciones y otra información de depuración. Este SDK proporciona también las tablas de referencia para las propiedades asociadas se encuentran en las aplicaciones de C++.  
  
 Para usar mejor el SDK de DIA, debe estar familiarizado con lo siguiente:  
  
- Lenguaje de programación de C++  
  
- Programación COM  
  
- Entorno de desarrollo integrado de Visual Studio (IDE) para compilar los ejemplos  
  
  El SDK de DIA normalmente se instala con Visual Studio y su ubicación predeterminada es *[unidad]* \Program Files\Microsoft 9.0\DIA de Visual Studio SDK. Como parte de la instalación, el msdia90.dll, que implementa el SDK de DIA, se registra automáticamente por lo que todo lo que necesita hacer para que lo utilice incluir `dia2.h` en su programa y vincularlo a `diaguids.lib`.  
  
  Encabezado: include\dia2.h  
  
  Library: lib\diaguids.lib  
  
  Archivo DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Revisa la arquitectura básica de DIA.  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones paso a paso sobre cómo usar la API de DIA para consultar un archivo. pdb.  
  
## <a name="see-also"></a>Vea también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)