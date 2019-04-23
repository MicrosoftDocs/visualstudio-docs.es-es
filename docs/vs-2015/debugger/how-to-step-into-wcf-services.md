---
title: Procedimiento Ir a servicios WCF | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 951d5f39fbf3929d094cc18de5fe108b46753b09
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60056450"
---
# <a name="how-to-step-into-wcf-services"></a>Procedimiento Depuración paso a paso por instrucciones de servicios WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], puede entrar en un servicio WCF. Si el servicio WCF está en la misma solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que el cliente, puede establecer puntos de interrupción dentro del servicio WCF.  
  
 Para que funcione la entrada en un servicio, debe tener la depuración habilitada en el archivo app.config o Web.config. Para obtener información acerca de cómo habilitar la depuración y para conocer las limitaciones de ir a servicios WCF, vea [limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Para entrar en un servicio WCF  
  
1. Cree una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contenga el cliente de WCF y los proyectos de servicio WCF.  
  
2. En el Explorador de soluciones, haga clic con el botón derecho del mouse en el proyecto Cliente WCF y, a continuación, haga clic en **Establecer como proyecto de inicio**.  
  
3. Habilite la depuración en el archivo app.config o web.config. Para obtener más información, consulte [limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4. Establezca un punto de interrupción en la ubicación del proyecto de cliente en la que desee iniciar la entrada. Normalmente, esto suele ser justo antes de la llamada al servicio WCF.  
  
5. Ejecute hasta el punto de interrupción y, a continuación, inicie la entrada. El depurador entrará en el servicio automáticamente.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de servicios WCF](../debugger/debugging-wcf-services.md)   
 [Limitaciones de la depuración de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Cómo: Depuración de un servicio WCF autohospedado](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
