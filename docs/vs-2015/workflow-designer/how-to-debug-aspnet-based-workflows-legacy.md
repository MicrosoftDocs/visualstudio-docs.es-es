---
title: Filtrar Depurar flujos de trabajo basados en ASP.NET (heredado) | Documentos de Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 25503430fd8924100a193ef5d8517231578800e0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58988814"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>Filtrar Depurar los flujos de trabajo basados en ASP.NET (heredado)
En este tema se describe cómo depurar aplicaciones [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] basadas en [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] en [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado.  
  
 Puede depurar flujos de trabajo heredados que se inician en ASP.NET o flujos de trabajo heredados que se publican como servicio Web adjuntándolos al proceso en el que está hospedado el flujo de trabajo.  
  
### <a name="to-debug-an-aspnet-based-workflow"></a>Para depurar un flujo de trabajo basado en ASP.NET  
  
1.  Habilitar la depuración de la aplicación ASP.NET estableciendo **debug = true** en el archivo web.config.  
  
2.  Establezca la biblioteca de flujos de trabajo como proyecto de inicio y establezca puntos de interrupción en el flujo de trabajo.  
  
3.  Escriba la dirección URL de la página Web predeterminada en las propiedades del proyecto de flujo de trabajo **depurar** opción **Iniciar explorador con la dirección URL externa** cuadro de texto.  
  
4.  Seleccione **asociar al proceso** en el **depurar** menú.  
  
5.  Seleccione el proceso para asociar en la **procesos disponibles** lista.  
  
     Adjunte al w3wp.exe, webdev.webserver o al proceso de aspnet_wp en que está hospedado el flujo de trabajo.  
  
6.  Haga clic en **seleccione** junto a la **adjuntar a** cuadro de texto.  
  
     El **Seleccionar tipo de código** aparece el cuadro de diálogo.  
  
7.  Seleccione **depurar estos tipos de código** y seleccione **flujo de trabajo**.  
  
8.  Haga clic en **Aceptar**.  
  
9. Haga clic en **Adjuntar**.  
  
10. Abra la página web predeterminada en un explorador e inicie el flujo de trabajo.  
  
## <a name="see-also"></a>Vea también  
 [Invocar al depurador de Visual Studio para Windows Workflow Foundation (heredado)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Cómo: Establecer puntos de interrupción en flujos de trabajo (heredado)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md)   
 [Depurar flujos de trabajo heredados](../workflow-designer/debugging-legacy-workflows.md)