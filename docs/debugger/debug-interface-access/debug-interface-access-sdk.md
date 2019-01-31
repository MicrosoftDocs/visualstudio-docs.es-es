---
title: Debug Interface Access SDK | Microsoft Docs
ms.date: 07/24/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 161934d30c7cd4ecb9d2658e7dac12e46049be1a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932303"
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
