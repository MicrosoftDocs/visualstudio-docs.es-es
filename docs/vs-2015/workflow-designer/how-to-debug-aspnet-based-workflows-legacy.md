---
title: 'Cómo: Depurar flujos de trabajo basados en ASP.NET (heredado) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668666"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Cómo: Depurar los flujos de trabajo basados en ASP.NET (Heredado)
En este tema se describe cómo depurar aplicaciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] basadas en [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado.

 Puede depurar flujos de trabajo heredados que se inician en ASP.NET o flujos de trabajo heredados que se publican como servicio Web adjuntándolos al proceso en el que está hospedado el flujo de trabajo.

### <a name="to-debug-an-aspnet-based-workflow"></a>Para depurar un flujo de trabajo basado en ASP.NET

1. Habilite la depuración para la aplicación ASP.NET estableciendo **debug = true** en el archivo de web.config.

2. Establezca la biblioteca de flujos de trabajo como proyecto de inicio y establezca puntos de interrupción en el flujo de trabajo.

3. Escriba la dirección URL de la página web predeterminada en el cuadro de texto de propiedades de proyecto de flujo de trabajo opción de **depuración** **iniciar explorador con dirección URL externa** .

4. Seleccione **asociar al proceso** en el menú **depurar** .

5. Seleccione el proceso al que desea asociar en la lista **procesos disponibles** .

     Adjunte al w3wp.exe, webdev.webserver o al proceso de aspnet_wp en que está hospedado el flujo de trabajo.

6. Haga clic en **seleccionar** junto al cuadro de texto **adjuntar a** .

     Aparece el cuadro de diálogo **Seleccionar tipo de código** .

7. Seleccione **depurar estos tipos de código** y seleccione **flujo de trabajo**.

8. Haga clic en **Aceptar**.

9. Haga clic en **Adjuntar**.

10. Abra la página web predeterminada en un explorador e inicie el flujo de trabajo.

## <a name="see-also"></a>Consulte también
 [Invocar el depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [Cómo: establecer puntos de interrupción en flujos de trabajo (heredado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)