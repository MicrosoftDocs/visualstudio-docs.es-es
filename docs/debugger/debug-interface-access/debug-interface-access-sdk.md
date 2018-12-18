---
title: Debug Interface Access SDK | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 279f5b883ca359c38ad8d357d153d02ea022b9da
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251671"
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK

El Microsoft depurar interfaz acceso Software Development Kit (SDK de DIA) proporciona acceso a información de depuración almacenada en archivos de programa (.pdb) de la base de datos generados por herramientas de postcompilador de Microsoft. Dado que el formato del archivo .pdb generado por las herramientas de postcompilador se somete a revisión constante, exponer el formato es práctico. Con la API de DIA, puede desarrollar aplicaciones que buscan y examen la información de depuración que se almacenan en un archivo. pdb. Estas aplicaciones, por ejemplo, podrían notificar la información de seguimiento back de pila y analizar datos de rendimiento.

## <a name="in-this-section"></a>En esta sección

[Introducción](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
Proporciona información general sobre el SDK de DIA características y especifica donde está instalado el SDK de DIA, así como los archivos de biblioteca y el encabezado necesario.

[Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
Proporciona instrucciones sobre cómo usar la API de DIA para consultar el archivo PDB.

[Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
Describe cómo se usan los símbolos y etiquetas de símbolo de la API de DIA.

[Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
Contiene las interfaces, métodos, enumeraciones y estructuras de la API de DIA.

[Ejemplo Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
Se muestra cómo usar la API de DIA para buscar y examinar la información de depuración.
