---
title: 'Cómo: Ir a servicios WCF | Microsoft Docs'
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
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cad65b893867a18133bbf9492a1c1786b24a81ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912169"
---
# <a name="how-to-step-into-wcf-services"></a>Cómo: Ir a servicios WCF
En [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], puede entrar en un servicio WCF. Si el servicio WCF está en la misma solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que el cliente, puede establecer puntos de interrupción dentro del servicio WCF.  
  
 Para que funcione la entrada en un servicio, debe tener la depuración habilitada en el archivo app.config o Web.config. Para obtener información acerca de cómo habilitar la depuración y para conocer las limitaciones de ir a servicios WCF, vea [limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Para entrar en un servicio WCF  
  
1. Cree una solución de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que contenga el cliente de WCF y los proyectos de servicio WCF.  
  
2. En el Explorador de soluciones, haga clic en el proyecto de cliente de WCF y, a continuación, haga clic en **establecer como proyecto de inicio**.  
  
3. Habilite la depuración en el archivo app.config o web.config. Para obtener más información, consulte [limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4. Establezca un punto de interrupción en la ubicación del proyecto de cliente en la que desee iniciar la entrada. Normalmente, esto suele ser justo antes de la llamada al servicio WCF.  
  
5. Ejecute hasta el punto de interrupción y, a continuación, inicie la entrada. El depurador entrará en el servicio automáticamente.  
  
## <a name="see-also"></a>Vea también  
 [Depurar servicios WCF](../debugger/debugging-wcf-services.md)   
 [Limitaciones sobre la depuración de WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Cómo: Depurar un servicio WCF independiente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)