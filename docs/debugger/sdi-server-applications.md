---
title: Aplicaciones de servidor SDI | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: 2b61b5797766a69e291c2d3d38500055890169a2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sdi-server-applications"></a>Aplicaciones de servidor SDI
Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en el **argumentos de línea de comandos** propiedad en el *proyecto* cuadro de diálogo de páginas de propiedades de C o C++, C#, o Proyectos de Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor. Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Encontrar la propiedad Argumentos de la línea de comandos  
 Para tener acceso a la *proyecto* cuadro de diálogo páginas de propiedades, haga clic en el proyecto en el Explorador de soluciones y, a continuación, elija Propiedades en el menú contextual. Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## <a name="see-also"></a>Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Cómo: Depurar servidores COM](../debugger/how-to-debug-com-servers.md)