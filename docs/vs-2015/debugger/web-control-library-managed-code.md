---
title: Biblioteca de controles (código administrado) Web | Microsoft Docs
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
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7e942fe6909d41ed5000f5e8a4f31f0de87cf9e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262535"
---
# <a name="web-control-library-managed-code"></a>Biblioteca de controles Web (código administrado)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La plantilla de proyecto Biblioteca de controles Web crea un archivo DLL. Como la biblioteca de clases es un archivo DLL, no se puede ejecutar directamente. Deberá crear una página de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que incruste el control. Para obtener más información, consulte [plantilla Biblioteca de controles Web](http://msdn.microsoft.com/en-us/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Para depurar una biblioteca de controles web (método 1)  
  
1.  Abra un proyecto de Biblioteca de controles Web existente o cree uno nuevo.  
  
2.  Cree una página de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] que incruste el control.  
  
3.  En el sitio Web donde se hospede el instrumento de prueba de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], cree un subdirectorio denominado `/Code`.  
  
4.  Copie el código fuente del control en el subdirectorio `/Code`.  
  
5.  Abra el código fuente del subdirectorio `/Code` y establezca puntos de interrupción.  
  
6.  Abra una ventana del explorador con una dirección URL que apunte al instrumento de prueba. Se alcanzará un punto de interrupción del control y podrá iniciar la depuración.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Para depurar una biblioteca de controles Web (método 2)  
  
1.  Cree el proyecto de aplicación host y el proyecto de control web en la misma solución.  
  
2.  En **el Explorador de soluciones**, haga clic en la aplicación host y elija **Agregar referencia**.  
  
3.  Agregue una referencia al proyecto de control Web.  
  
## <a name="see-also"></a>Vea también  
 [Aplicaciones web de ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)



