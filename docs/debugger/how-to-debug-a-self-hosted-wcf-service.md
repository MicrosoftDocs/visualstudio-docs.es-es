---
title: para depurar un servicio WCF autohospedado | Microsoft Docs
description: Vea cómo depurar un servicio WCF autohospedado. La manera más fácil (pero no siempre posible) es configurar Visual Studio para que inicie tanto el cliente como el servidor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3cd11966347cd90576eb78a59f6c7eb96cc697ef
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155086"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Procedimiento Depuración de un servicio WCF autohospedado
Un *servicio que se hospeda a sí mismo* es un servicio WCF que no se ejecuta dentro de IIS, el host de servicio WCF o el servidor de desarrollo de [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. La manera más fácil de depurar un WCF que se hospeda a sí mismo es configurar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para que inicie tanto el cliente como el servidor si elige **Iniciar depuración** en el menú **Depurar**.

 Si el servicio WCF se hospeda a sí mismo dentro de un proceso que no se puede iniciar de esta manera, por ejemplo un servicio NT, no podrá utilizar este método. En su lugar, puede realizar uno de los siguientes procedimientos:

- Asociar manualmente el depurador al proceso que hospeda. Para obtener más información, vea [Asociación con procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     o

- Empezar a depurar el cliente y, a continuación, entrar en una llamada al servicio. Esto requiere habilitar la depuración en el archivo app.config. Para obtener más información, vea [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Para iniciar el cliente y el host desde Visual Studio

1. Cree una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contenga los proyectos de cliente y servidor.

2. Configure la solución para iniciar los procesos de cliente y servidor al elegir **Inicio** en el menú **Depurar**.

   1. En el **Explorador de soluciones**, haga clic con el botón derecho del mouse en el nombre de la solución.

   2. Haga clic en **Establecer proyectos de inicio**.

   3. En el cuadro de diálogo **Solución \<name> Propiedades**, seleccione **Proyectos de inicio múltiples**.

   4. En la cuadrícula **Proyectos de inicio múltiples**, en la línea que corresponde al proyecto de servidor, haga clic en **Acción** y elija **Inicio**.

   5. En la línea que corresponde al proyecto de cliente, haga clic en **Acción** y elija **Inicio**.

   6. Haga clic en **Aceptar**.

## <a name="see-also"></a>Vea también
- [Depurar servicios WCF](../debugger/debugging-wcf-services.md)
- [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md)
- [Cómo: Depuración paso a paso por instrucciones de servicios WCF](../debugger/how-to-step-into-wcf-services.md)
