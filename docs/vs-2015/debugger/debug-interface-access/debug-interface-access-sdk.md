---
title: Debug Interface Access SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ddaea95bc879364de99c0ec01213cda30fa4e7d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197621"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El kit de desarrollo de software de Microsoft Debug interface Access (SDK de DIA) proporciona acceso a la información de depuración almacenada en archivos de base de datos de programa (. pdb) generados por las herramientas de Microsoft postcompiler. Dado que el formato del archivo. pdb generado por las herramientas de postcompilador sufre una revisión constante, exponer el formato no es práctico. Con la API de DIA, puede desarrollar aplicaciones que busquen y examinen la información de depuración almacenada en un archivo. pdb. Tales aplicaciones podrían, por ejemplo, notificar la información de seguimiento de la pila y analizar los datos de rendimiento.  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Proporciona información general sobre las características del SDK de DIA y especifica dónde se instala el SDK de DIA, así como los archivos de encabezado y de biblioteca necesarios.  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones sobre cómo usar la API de DIA para consultar el archivo. pdb.  
  
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Describe cómo se usan símbolos y etiquetas de símbolos en la API DIA.  
  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contiene las interfaces, los métodos, las enumeraciones y las estructuras de la API de DIA.  
  
 [Ejemplo Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Muestra cómo usar la API de DIA para buscar y examinar la información de depuración.  
  
 [Archivo de origen Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Código fuente utilizado por el [ejemplo de Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) para mostrar la API de dia.
