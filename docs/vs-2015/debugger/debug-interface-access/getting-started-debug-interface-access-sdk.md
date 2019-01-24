---
title: Introducción (Debug Interface Access SDK) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- .dbg files
- DBG files
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b5b04868bac6e27e5badd690d84cdc21722c723
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753096"
---
# <a name="getting-started-debug-interface-access-sdk"></a>Introducción (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El Debug Interface Access (DIA) SDK proporciona documentación con instrucciones y un ejemplo que ilustra cómo usar la API de DIA. Use las interfaces y métodos en el SDK de DIA para desarrollar aplicaciones personalizadas que abrir los archivos .pdb y .dbg y buscar su contenido para los símbolos, valores, atributos, las direcciones y otra información de depuración. Este SDK proporciona también las tablas de referencia para las propiedades asociadas se encuentran en las aplicaciones de C++.  
  
 Para usar mejor el SDK de DIA, debe estar familiarizado con lo siguiente:  
  
- Lenguaje de programación de C++  
  
- Programación COM  
  
- Entorno de desarrollo integrado de Visual Studio (IDE) para compilar los ejemplos  
  
  El SDK de DIA normalmente se instala con Visual Studio y su ubicación predeterminada es *[unidad]* \Program Files\Microsoft 9.0\DIA de Visual Studio SDK. Como parte de la instalación, el msdia90.dll, que implementa el SDK de DIA, se registra automáticamente por lo que todo lo que necesita hacer para que lo utilice incluir `dia2.h` en su programa y vincularlo a `diaguids.lib`.  
  
  Encabezado: include\dia2.h  
  
  Biblioteca: lib\diaguids.lib  
  
  Archivo DLL: bin\msdia80.dll  
  
  IDL: idl\dia2.idl  
  
## <a name="in-this-section"></a>En esta sección  
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Revisa la arquitectura básica de DIA.  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones paso a paso sobre cómo usar la API de DIA para consultar un archivo. pdb.  
  
## <a name="see-also"></a>Vea también  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)



