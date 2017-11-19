---
title: Diferencias entre en un espacio aislado y soluciones de granja | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
ms.assetid: 43beb7e7-0cd9-4a8f-bb72-6b1e0cba5be8
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d82bc012b2be9736b83fc07f7d0a83d354dda002
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Diferencias entre soluciones en espacio aislado y soluciones de granja
  Cuando se compila una solución de SharePoint, se implementa en el servidor de SharePoint y se adjunta un depurador para depurarlo. El proceso que se utiliza para depurar la solución depende del valor de la propiedad de la solución en espacio aislado: solución en espacio aislado o una solución de granja de servidores.  
  
 Para obtener más información, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Soluciones de granja de servidores  
 Soluciones de granja de servidores, que se hospedan en el proceso de trabajo IIS (W3WP.exe), ejecutan el código que puede afectar a toda la granja. Cuando se depura un proyecto de SharePoint cuya propiedad solución en espacio aislado se establece en "solución de granja de servidores", se recicla el grupo de aplicaciones de IIS del sistema antes de que SharePoint se retira o implementa la característica con el fin de liberar los archivos bloqueados por el proceso de trabajo IIS. Solo el grupo de aplicaciones IIS que sirve al dirección URL del sitio del proyecto de SharePoint se recicla.  
  
## <a name="sandboxed-solutions"></a>Soluciones en espacio aislado  
 Soluciones en espacio aislado, que se hospedan en el proceso de trabajo de solución (SPUCWorkerProcess.exe) del código de usuario de SharePoint, ejecutan código que solo puede afectar a la colección de sitios de la solución. Dado que las soluciones en espacio aislado no se ejecutan en el proceso de trabajo IIS, debe reiniciar el grupo de aplicaciones de IIS ni el servidor IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]asocia al depurador al proceso SPUCWorkerProcess que desencadena automáticamente el servicio SPUserCodeV4 en SharePoint y controles. No es necesario para el proceso SPUCWorkerProcess se recicle para cargar la versión más reciente de la solución.  
  
## <a name="either-type-of-solution"></a>Cualquier tipo de solución  
 Con cualquier tipo de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también asocia el depurador al explorador para habilitar la depuración de script de cliente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]usa el motor para este propósito de depuración de script. Para habilitar la depuración de script, debe cambiar la configuración predeterminada del explorador cuando se le pida.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]asocia al depurador solo a los procesos de W3WP o SPUCWorkerProcess ejecutando el sitio actual. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]también asocia el flujo de trabajo de motores de depuración y COM Plus administrado.  
  
## <a name="see-also"></a>Vea también  
 [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md)  
  
  