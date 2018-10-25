---
title: Deshabilitar el depurador Just-In-Time | Microsoft Docs
ms.custom: ''
ms.date: 05/23/18
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 147e16bab14a6a038622804cf9c57e5fdc92bf02
ms.sourcegitcommit: c5e72875206b8c5737c29d5b1ec7b86eec747303
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/17/2018
ms.locfileid: "49382784"
---
# <a name="disable-the-just-in-time-debugger"></a>Deshabilitar al depurador Just-In-Time 

El cuadro de diálogo de depurador Just In Time puede abrir cuando se produce un error en una aplicación en ejecución y evitará que continúe la aplicación. 

El depurador Just In Time le ofrece la opción para iniciar Visual Studio para depurar el error. Debe tener [Visual Studio](http://visualstudio.microsoft.com) u otro depurador seleccionado instalado para ver información detallada sobre el error o intente depurarla. 

Si es un usuario de Visual Studio y desea intentar depurar el error, vea [depurar con el depurador Just In Time](../debugger/debug-using-the-just-in-time-debugger.md). Si no se puede corregir el error, o desea conservar el depurador Just In Time de apertura, también puede [Just-In-Time de deshabilitar la depuración desde Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling). 

Si ha instalado Visual Studio, pero ya no es no, es posible que deba [Just-In-Time de deshabilitar la depuración desde el registro de Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry). 

Si no tiene instalado Visual Studio, puede evitar deshabilitando la depuración de scripts o depuración de servidor de depuración Just-In-Time. 

- Si está intentando ejecutar una aplicación web, deshabilite la depuración de script:
  
  En Windows **Panel de Control** > **red e Internet** > **opciones de Internet**, seleccione **Disable (depuración de script Internet Explorer)** y **Deshabilitar depuración de scripts (otros)**. La configuración y los pasos exactos depende de la versión de Windows y el explorador.
  
  ![Las opciones de Internet de JIT](../debugger/media/jitinternetoptions.png "opciones de internet JIT")
  
- Si está hospedando una aplicación web ASP.NET en IIS, deshabilitar la depuración de servidor:

  1. En el Administrador de IIS **vista características**, en el **ASP.NET** sección, haga doble clic en **compilación .NET**, o selecciónelo y, a continuación, seleccione **abrir característica**en el **acciones** panel. 
  1. En **comportamiento** > **depurar**, seleccione **False**. Los pasos son diferentes en versiones anteriores de IIS.

Después de deshabilitar la depuración Just-In-Time, la aplicación puede ser capaz de controlar el error y ejecute normalmente. 

Si la aplicación todavía tiene un error no controlado, verá un mensaje de error o la aplicación puede bloquearse o de bloqueo. La aplicación no se ejecuta con normalidad hasta que se ha corregido el error. Puede intentar ponerse en contacto con el propietario de la aplicación y pídale que lo corrija.

