---
title: 'Cómo: Ir a servicios WCF | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- debugging, WCF
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b779c8bc2e6da3975f1f70265482c706c9141375
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577172"
---
# <a name="how-to-step-into-wcf-services"></a>Cómo: Ir a servicios WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: Ir a servicios WCF](https://docs.microsoft.com/visualstudio/debugger/how-to-step-into-wcf-services).  
  
En [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], puede entrar en un servicio WCF. Si el servicio WCF está en la misma solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que el cliente, puede establecer puntos de interrupción dentro del servicio WCF.  
  
 Para que funcione la entrada en un servicio, debe tener la depuración habilitada en el archivo app.config o Web.config. Para obtener información acerca de cómo habilitar la depuración y para conocer las limitaciones de ir a servicios WCF, vea [limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Para entrar en un servicio WCF  
  
1.  Cree una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que contenga el cliente de WCF y los proyectos de servicio WCF.  
  
2.  En el Explorador de soluciones, haga clic en el proyecto de cliente de WCF y, a continuación, haga clic en **establecer como proyecto de inicio**.  
  
3.  Habilite la depuración en el archivo app.config o web.config. Para obtener más información, consulte [limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Establezca un punto de interrupción en la ubicación del proyecto de cliente en la que desee iniciar la entrada. Normalmente, esto suele ser justo antes de la llamada al servicio WCF.  
  
5.  Ejecute hasta el punto de interrupción y, a continuación, inicie la entrada. El depurador entrará en el servicio automáticamente.  
  
## <a name="see-also"></a>Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Cómo: Depurar un servicio WCF independiente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



