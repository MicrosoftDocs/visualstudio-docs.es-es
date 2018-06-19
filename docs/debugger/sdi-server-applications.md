---
title: Aplicaciones de servidor SDI | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: 9047c9b39bad5f4f790327b5ee65b4de688db9d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
ms.locfileid: "31475667"
---
# <a name="sdi-server-applications"></a>Aplicaciones de servidor SDI
Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en el **argumentos de línea de comandos** propiedad en el *proyecto* cuadro de diálogo de páginas de propiedades de C o C++, C#, o Proyectos de Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor. Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Encontrar la propiedad Argumentos de la línea de comandos  
 Para tener acceso a la *proyecto* cuadro de diálogo páginas de propiedades, haga clic en el proyecto en el Explorador de soluciones y, a continuación, elija Propiedades en el menú contextual. Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## <a name="see-also"></a>Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Cómo: Depurar servidores COM](../debugger/how-to-debug-com-servers.md)