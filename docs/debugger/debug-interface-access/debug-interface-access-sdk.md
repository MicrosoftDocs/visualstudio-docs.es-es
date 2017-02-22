---
title: "Debug Interface Access SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "depurar [Kit de desarrollo DIA (SDK)]"
  - "depurador [Kit de desarrollo DIA (SDK)]"
  - "Kit de desarrollo DIA (SDK)"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug Interface Access SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El kit de desarrollo de software de Access de la interfaz de depuración de Microsoft \(diámetro SDK\) proporciona acceso a información de depuración almacenada en los archivos de base de datos de programa \(.pdb\) generados por herramientas de postcompiler de Microsoft.  Porque el formato del archivo .pdb generado por las herramientas de postcompiler experimenta la revisión constante, exponer el formato es poco práctico.  Mediante el diámetro API, puede desarrollar aplicaciones que buscan y examine la información de depuración almacenada en un archivo .pdb.  Dichas aplicaciones podrían, por ejemplo, enviar información de la informes de seguimiento de la pila y analizar los datos de rendimiento.  
  
## En esta sección  
 [Introducción](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Proporciona información general sobre las características del diámetro SDK y especifica dónde el diámetro SDK está instalado junto con el encabezado y los archivos de biblioteca necesarios.  
  
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Proporciona instrucciones sobre cómo utilizar el diámetro API para ver el archivo .pdb.  
  
 [Símbolos y etiquetas de símbolo](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Explica cómo los símbolos y etiquetas de símbolos se utilizan en el diámetro API.  
  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contiene interfaces, métodos, enumeraciones, y estructuras de diámetro API.  
  
 [Ejemplo Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Muestra cómo utilizar el diámetro API para buscar y examinar información de depuración.  
  
 [Archivo de origen Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Código fuente utilizado por [Ejemplo Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) para mostrar el diámetro API.