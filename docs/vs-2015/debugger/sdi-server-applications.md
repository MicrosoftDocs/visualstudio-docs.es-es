---
title: Aplicaciones de servidor SDI | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ea0497c7d20c0102aff3bc77cdecf87d1525a82c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752405"
---
# <a name="sdi-server-applications"></a>Aplicaciones de servidor SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en el **argumentos de línea de comandos** propiedad en el *proyecto* cuadro de diálogo páginas de propiedades para C/C ++, C#, o Proyectos de Visual Basic.  
  
 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor. Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.  
  
## <a name="finding-the-command-line-arguments-property"></a>Encontrar la propiedad Argumentos de la línea de comandos  
 Para tener acceso a la *proyecto* cuadro de diálogo páginas de propiedades, haga clic en el proyecto en el Explorador de soluciones y, a continuación, elija Propiedades en el menú contextual. Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.  
  
## <a name="see-also"></a>Vea también  
 [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)   
 [Cómo: Depurar servidores COM](../debugger/how-to-debug-com-servers.md)



