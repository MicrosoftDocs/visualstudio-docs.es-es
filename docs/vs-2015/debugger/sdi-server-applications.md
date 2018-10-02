---
title: Aplicaciones de servidor SDI | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c6ee3ee3a1273c02dd094f89c099230024eabfc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47582040"
---
# <a name="sdi-server-applications"></a>Aplicaciones de servidor SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [aplicaciones de servidor SDI](https://docs.microsoft.com/visualstudio/debugger/sdi-server-applications).  
  
Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en el **argumentos de línea de comandos** propiedad en el *proyecto* cuadro de diálogo páginas de propiedades para C/C ++, C#, o Proyectos de Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor. Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Encontrar la propiedad Argumentos de la línea de comandos  
 Para tener acceso a la *proyecto* cuadro de diálogo páginas de propiedades, haga clic en el proyecto en el Explorador de soluciones y, a continuación, elija Propiedades en el menú contextual. Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## <a name="see-also"></a>Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Cómo: Depurar servidores COM](../debugger/how-to-debug-com-servers.md)



