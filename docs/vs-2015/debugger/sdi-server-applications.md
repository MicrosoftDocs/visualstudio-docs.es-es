---
title: Aplicaciones de servidor SDI | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148147"
---
# <a name="sdi-server-applications"></a>Aplicaciones de servidor SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en la propiedad **Argumentos de la línea de comandos** del cuadro de diálogo Páginas de propiedades de *proyecto* de los proyectos de C/C++, C# o Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor. Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Encontrar la propiedad Argumentos de la línea de comandos  
 Para tener acceso al cuadro de diálogo Páginas de propiedades de *proyecto*, haga clic con el botón derecho en el proyecto desde el Explorador de soluciones y después elija Propiedades en el menú contextual. Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## <a name="see-also"></a>Consulte también  
 [Depuración COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Cómo: depurar servidores COM](../debugger/how-to-debug-com-servers.md)
