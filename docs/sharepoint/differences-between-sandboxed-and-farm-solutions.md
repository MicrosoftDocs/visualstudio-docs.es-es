---
title: Diferencias entre el espacio aislado y soluciones de granja | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f4f37d908448eba54924589cd669dbdda84956d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53849754"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Diferencias entre el espacio aislado y soluciones de granja
  Al compilar una solución de SharePoint, se implementa en el servidor de SharePoint y se adjunta un depurador para depurarlo. El proceso puede utilizado para depurar la solución depende de la configuración de la propiedad solución en espacio aislado: solución en espacio aislado o una solución de granja de servidores.  
  
 Para obtener más información, consulte [consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Soluciones de granja
 Soluciones de granja de servidores, que se hospedan en el proceso de trabajo IIS (W3WP.exe), ejecutan el código que puede afectar a toda la granja. Cuando se depura un proyecto de SharePoint cuya propiedad solución en espacio aislado se establece en "solución de granja de servidores", grupo de aplicaciones de IIS del sistema se recicla antes de que SharePoint se retira o implementa la característica para liberar los archivos bloqueados por el proceso de trabajo IIS. Solo el grupo de aplicaciones de IIS que actúa la dirección URL del sitio del proyecto de SharePoint se recicla.  
  
## <a name="sandboxed-solutions"></a>Soluciones en espacio aislado
 Soluciones en espacio aislado, que se hospedan en el proceso de trabajo de solución (SPUCWorkerProcess.exe) del código de usuario de SharePoint, ejecutan código que solo puede afectar a la colección de sitios de la solución. Dado que las soluciones en espacio aislado no se ejecutan en el proceso de trabajo IIS, debe reiniciar el grupo de aplicaciones de IIS ni el servidor IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] asocia al depurador al proceso SPUCWorkerProcess que desencadena automáticamente el servicio SPUserCodeV4 en SharePoint y los controles. No es necesario para el proceso SPUCWorkerProcess se recicle para cargar la versión más reciente de la solución.  
  
## <a name="either-type-of-solution"></a>Cualquier tipo de solución
 Con cualquier tipo de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también asocia el depurador al explorador para habilitar la depuración de script de cliente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa el script de depuración motor para este propósito. Para habilitar la depuración de script, debe cambiar la configuración predeterminada del explorador cuando se le pida.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] asocia al depurador solo a los procesos de W3WP o SPUCWorkerProcess ejecutando el sitio actual. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también asocia el flujo de trabajo de los motores de depuración y COM Plus administrado.  
  
## <a name="see-also"></a>Vea también
 [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Compilar y depurar soluciones de SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Consideraciones sobre la solución en espacio aislado](../sharepoint/sandboxed-solution-considerations.md)  
