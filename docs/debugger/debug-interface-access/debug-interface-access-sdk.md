---
title: Debug Interface Access SDK | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cd84741d006304f7dfefe8ee4a1060ba64ffdb8b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK
El Microsoft depurar interfaz acceso Software Development Kit (SDK de DIA) proporciona acceso a información de depuración almacenada en archivos de programa (.pdb) de la base de datos generados por herramientas de postcompilador de Microsoft. Dado que el formato del archivo .pdb generado por las herramientas de postcompilador sufre constante revisión, resulta poco práctico exponer el formato. Con la API de DIA, puede desarrollar aplicaciones que buscan y examen información de depuración almacenada en un archivo .pdb. Dichas aplicaciones podrían, por ejemplo, proporcionan información de devolución de seguimiento de pila y analizar datos de rendimiento.  
  
## <a name="in-this-section"></a>En esta sección  
 [Introducción](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Proporciona información general sobre el SDK de DIA características y especifica donde está instalado el SDK de DIA, así como los archivos de biblioteca y el encabezado necesario.  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones sobre cómo usar la API de DIA para consultar el archivo PDB.  
  
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Describe cómo se utilizan los símbolos y etiquetas de símbolo de la API de DIA.  
  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contiene las interfaces, métodos, enumeraciones y estructuras de la API de DIA.  
  
 [Ejemplo Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Muestra cómo utilizar la API de DIA para buscar y examinar la información de depuración.  
  
 [Archivo de origen Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Utilizado por el código fuente [ejemplo Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) para demostrar la API de DIA.