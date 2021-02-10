---
title: Deshabilitar el depurador Just-In-Time | Microsoft Docs
description: El cuadro de diálogo Depurador Just-in-Time puede abrirse cuando se produce un error en una aplicación. Obtenga información sobre qué puede hacer cuando esto sucede y sobre las formas de evitarlo.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670809ea2c9ef04107dbec5634f40831b68b94c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931505"
---
# <a name="disable-the-just-in-time-debugger"></a>Deshabilitar el depurador Just-In-Time

El cuadro de diálogo del depurador Just-In-Time puede abrirse cuando se produce un error en una aplicación en ejecución e impedir que la aplicación continúe funcionando.

El depurador Just-in-Time le ofrece la opción de iniciar Visual Studio para depurar el error. Debe tener instalado Visual Studio u otro depurador seleccionado para ver información detallada sobre el error o para intentar depurarlo.

Si ya es usuario de Visual Studio y quiere intentar depurar el error, vea el artículo [Depuración con el depurador Just-In-Time en Visual Studio](../debugger/debug-using-the-just-in-time-debugger.md). Si no puede corregir el error o quiere impedir que el depurador Just-in-Time se abra, puede [deshabilitar la depuración Just-in-Time desde Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Si tiene Visual Studio instalado pero ya no lo quiere, puede [deshabilitar la depuración Just-in-Time en el registro de Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Si no tiene instalado Visual Studio, puede impedir la depuración Just-in-Time deshabilitando la depuración de scripts o la depuración del lado servidor.

- Si está intentando ejecutar una aplicación web, deshabilite la depuración de scripts:

  En **Panel de control de Windows** > **Redes e Internet** > **Opciones de Internet**, seleccione **Deshabilitar la depuración de scripts (Internet Explorer)** y **Deshabilitar la depuración de scripts (otros)** . Los pasos y la configuración exactos dependen de la versión de Windows y del explorador.

  ![Opciones de Internet Just-in-Time](../debugger/media/jitinternetoptions.png "Opciones de Internet Just-in-Time")

- Si hospeda una aplicación web ASP.NET en IIS, deshabilite la depuración del lado servidor:

  1. En la **Vista Características** del Administrador de IIS, en la sección **ASP.NET**, haga doble clic en **Compilación de .NET** o seleccione esta opción y, después, seleccione **Abrir característica** en el panel **Acciones**.
  1. En **Comportamiento** > **Depurar**, seleccione **Falso**. Los pasos son diferentes en versiones anteriores de IIS.

Después de deshabilitar la depuración Just-in-Time, la aplicación puede ser capaz de controlar el error y ejecutarse con normalidad.

Si la aplicación todavía presenta un error no controlado, puede ser que vea un mensaje de error o que la aplicación se bloquee o deje de responder. La aplicación no se ejecutará con normalidad hasta que se corrija el error. Puede intentar contactar con el propietario de la aplicación y pedirle que la corrija.
