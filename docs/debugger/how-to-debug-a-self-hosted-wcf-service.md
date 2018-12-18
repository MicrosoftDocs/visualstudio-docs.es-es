---
title: 'Cómo: depurar un servicio WCF Autohospedado | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 255ca0f7d472060d110135536d76de99dc46a18e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872127"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Cómo: Depurar un servicio WCF independiente
Un *autohospedado servicio* es un servicio WCF que no se ejecuta dentro de IIS, el Host de servicio WCF o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] servidor de desarrollo. La manera más fácil de depurar un WCF autohospedado es configurar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para iniciar el cliente y servidor cuando se elige **Iniciar depuración** en el **depurar** menú.  
  
 Si el servicio WCF se hospeda a sí mismo dentro de un proceso que no se puede iniciar de esta manera, por ejemplo un servicio NT, no podrá utilizar este método. En su lugar, puede realizar uno de los siguientes procedimientos:  
  
-   Asociar manualmente el depurador al proceso que hospeda. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     o  
  
-   Empezar a depurar el cliente y, a continuación, entrar en una llamada al servicio. Esto requiere habilitar la depuración en el archivo app.config. Para obtener más información, [limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Para iniciar el cliente y el host desde Visual Studio  
  
1. Cree una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contenga los proyectos de cliente y servidor.  
  
2. Configurar la solución para iniciar los procesos de cliente y servidor cuando se elige **iniciar** en el **depurar** menú.  
  
   1.  En **el Explorador de soluciones**, haga clic en el nombre de la solución.  
  
   2.  Haga clic en **Establecer proyectos de inicio**.  
  
   3.  En el **solución \<nombre > propiedades** cuadro de diálogo, seleccione **varios proyectos de inicio**.  
  
   4.  En el **varios proyectos de inicio** cuadrícula, en la línea que corresponde al proyecto de servidor, haga clic en **acción** y elija **iniciar**.  
  
   5.  En la línea que corresponde al proyecto de cliente, haga clic en **acción** y elija **iniciar**.  
  
   6.  Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Cómo: Ir a servicios WCF](../debugger/how-to-step-into-wcf-services.md)