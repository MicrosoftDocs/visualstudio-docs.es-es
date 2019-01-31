---
title: Procedimiento Deshabilitar el proceso de hospedaje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0266e14b3a03e6d8225e7ec9283fe727a9502e53
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785886"
---
# <a name="how-to-disable-the-hosting-process"></a>Procedimiento Deshabilitar el proceso de hospedaje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las llamadas a ciertas API pueden verse afectadas cuando se habilita el proceso de hospedaje. En estos casos, es necesario deshabilitar el proceso de hospedaje para devolver los resultados correctos.  
  
### <a name="to-disable-the-hosting-process"></a>Para deshabilitar el proceso de hospedaje  
  
1. Abra un proyecto ejecutable en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Los proyectos que no generan archivos ejecutables (por ejemplo, proyectos de biblioteca de clases o de servicio) no tienen esta opción.  
  
2. En el menú **Proyecto**, haga clic en **Propiedades**.  
  
3. Haga clic en la pestaña **Depurar**.  
  
4. Desactive la casilla **Habilitar el proceso de hospedaje de Visual Studio**.  
  
   Cuando se deshabilita el proceso de hospedaje, varias características de depuración no están disponibles o sufren una disminución de rendimiento. Para obtener más información, consulte [Depuración y proceso de hospedaje](../debugger/debugging-and-the-hosting-process.md).  
  
   En general, cuando se deshabilita el proceso de hospedaje:  
  
-   Aumenta el tiempo necesario para empezar a depurar las aplicaciones de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
-   No está disponible la evaluación de expresiones en tiempo de diseño.  
  
-   No está disponible la depuración de confianza parcial.  
  
## <a name="see-also"></a>Vea también  
 [Depuración y proceso de hospedaje](../debugger/debugging-and-the-hosting-process.md)   
 [Proceso de alojamiento (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Versiones de compilación durante el desarrollo de una aplicación](http://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
