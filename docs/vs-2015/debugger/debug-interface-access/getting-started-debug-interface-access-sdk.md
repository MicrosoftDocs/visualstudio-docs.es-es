---
title: Introducción (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54f83f00ed2e99d1541e15092cb3ee0ce9e08952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164167"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introducción (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El SDK de Debug interface Access (DIA) le proporciona documentación de instrucciones y un ejemplo que muestra cómo usar la API de DIA. Use las interfaces y los métodos del SDK de DIA para desarrollar aplicaciones personalizadas que abran los archivos. PDB y. dbg y busque en su contenido símbolos, valores, atributos, direcciones y otra información de depuración. Este SDK también proporciona tablas de referencia para las propiedades asociadas a los símbolos que se encuentran en las aplicaciones de C++.  
  
 Para usar mejor el SDK de DIA, debe estar familiarizado con lo siguiente:  
  
- Lenguaje de programación C++  
  
- Programación COM  
  
- Entorno de desarrollo integrado (IDE) de Visual Studio para compilar los ejemplos  
  
  El SDK de DIA se instala normalmente con Visual Studio y su ubicación predeterminada es *[unidad]* \Archivos de Programa\microsoft Visual Studio 9.0 \ dia SDK. Como parte de la instalación, el msdia90.dll, que implementa el SDK de DIA, se registra automáticamente, por lo que todo lo que debe hacer para usarlo es incluirlo `dia2.h` en el programa y vincularlo a `diaguids.lib` .  
  
  Encabezado: include\dia2.h  
  
  Biblioteca: lib\diaguids.lib  
  
  DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Revisa la arquitectura básica de DIA.  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones paso a paso sobre cómo usar la API de DIA para consultar un archivo. pdb.  
  
## <a name="see-also"></a>Consulte también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)
