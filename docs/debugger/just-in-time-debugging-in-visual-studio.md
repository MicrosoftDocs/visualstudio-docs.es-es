---
title: Deshabilitar el depurador Just-in-Time | Microsoft Docs
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb66615abbd7124fd6b781598bd8eb28ea34756d
ms.sourcegitcommit: 0b90e1197173749c4efee15c2a75a3b206c85538
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2019
ms.locfileid: "74903870"
---
# <a name="disable-the-just-in-time-debugger"></a>Deshabilitar el depurador Just-In-Time

El cuadro de diálogo del depurador Just-in-Time puede abrirse cuando se produce un error en una aplicación en ejecución y evitar que la aplicación continúe.

El depurador Just-in-Time le ofrece la opción de iniciar Visual Studio para depurar el error. Debe tener instalado Visual Studio u otro depurador seleccionado para ver información detallada sobre el error o intentar depurarlo.

Si ya es usuario de Visual Studio y desea intentar depurar el error, consulte depurar [mediante el depurador Just-in-Time](../debugger/debug-using-the-just-in-time-debugger.md). Si no puede corregir el error o desea mantener la apertura del depurador Just-in-Time, puede [deshabilitar la depuración Just-in-Time desde Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Si tiene Visual Studio instalado pero ya no lo hace, es posible que tenga que [deshabilitar la depuración Just-in-Time en el registro de Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Si no tiene instalado Visual Studio, puede impedir la depuración Just-in-Time deshabilitando la depuración de scripts o la depuración del lado servidor.

- Si está intentando ejecutar una aplicación Web, deshabilite la depuración de scripts:

  En el **Panel de control** de Windows > opciones **de red e Internet** > **Internet**, seleccione **deshabilitar la depuración de scripts (Internet Explorer)** y **deshabilitar la depuración de scripts (otros)** . Los pasos y la configuración exactos dependen de la versión de Windows y del explorador.

  ![Opciones de Internet JIT](../debugger/media/jitinternetoptions.png "Opciones de Internet JIT")

- Si va a hospedar una aplicación Web de ASP.NET en IIS, deshabilite la depuración del servidor:

  1. En la **vista características**del administrador de IIS, en la sección **ASP.net** , haga doble clic en **compilación de .net**o selecciónela y, a continuación, seleccione **abrir característica** en el panel **acciones** .
  1. En **comportamiento** > **depurar**, seleccione **falso**. Los pasos son diferentes en versiones anteriores de IIS.

Después de deshabilitar la depuración Just-in-Time, es posible que la aplicación pueda controlar el error y ejecutarse con normalidad.

Si la aplicación todavía tiene un error no controlado, puede ver un mensaje de error o la aplicación puede bloquearse o bloquearse. La aplicación no se ejecutará normalmente hasta que se solucione el error. Puede intentar ponerse en contacto con el propietario de la aplicación y pedirles que la corrijan.
