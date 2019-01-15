---
title: Aplicaciones de servidor SDI | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ec4178fb23d84812d7258bac8384264bed9d4690
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53885066"
---
# <a name="sdi-server-applications"></a>Aplicaciones de servidor SDI
Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en la propiedad **Argumentos de la línea de comandos** del cuadro de diálogo Páginas de propiedades de *proyecto* de los proyectos de C/C++, C# o Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor. Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Encontrar la propiedad Argumentos de la línea de comandos  
 Para tener acceso al cuadro de diálogo Páginas de propiedades de *proyecto*, haga clic con el botón derecho en el proyecto desde el Explorador de soluciones y después elija Propiedades en el menú contextual. Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Cómo: Depuración de servidores COM](../debugger/how-to-debug-com-servers.md)