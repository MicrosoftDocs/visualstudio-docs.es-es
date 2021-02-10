---
title: Diferencias entre soluciones en espacio aislado y soluciones de granja | Microsoft Docs
description: Comprenda las diferencias entre las soluciones en espacio aislado y las soluciones de granja. Sepa cómo Visual Studio se aproxima a la depuración con cualquier tipo de solución.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cea66f313a8c6c8ad7fc390a3ca126d92139725c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948783"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Diferencias entre soluciones en espacio aislado y soluciones de granja
  Al compilar una solución de SharePoint, se implementa en el servidor de SharePoint y un depurador se adjunta para depurarla. El proceso usado para depurar la solución depende del valor de la propiedad de la solución en espacio aislado: solución en espacio aislado o solución de granja.

 Para obtener más información, vea [consideraciones sobre las soluciones en espacio aislado](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Soluciones de granja
 Las soluciones de granja de servidores, que se hospedan en el proceso de trabajo de IIS (W3WP.exe), ejecutan código que puede afectar a toda la granja. Al depurar un proyecto de SharePoint cuya propiedad de solución en espacio aislado está establecida en "solución de granja", el grupo de aplicaciones de IIS del sistema se recicla antes de que SharePoint retraiga o implemente la característica para liberar los archivos bloqueados por el proceso de trabajo de IIS. Solo se recicla el grupo de aplicaciones de IIS que da servicio a la dirección URL del sitio del proyecto de SharePoint.

## <a name="sandboxed-solutions"></a>Soluciones en espacio aislado
 Las soluciones en espacio aislado, que se hospedan en el proceso de trabajo de solución de código de usuario de SharePoint (SPUCWorkerProcess.exe), ejecutan código que solo puede afectar a la colección de sitios de la solución. Dado que las soluciones en espacio aislado no se ejecutan en el proceso de trabajo de IIS, ni el grupo de aplicaciones de IIS ni el servidor IIS deben reiniciarse. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] asocia el depurador al proceso SPUCWorkerProcess que el servicio SPUserCodeV4 de SharePoint desencadena y controla automáticamente. No es necesario que el proceso SPUCWorkerProcess se recicle para cargar la versión más reciente de la solución.

## <a name="either-type-of-solution"></a>Cualquier tipo de solución
 Con cualquier tipo de solución, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también asocia el depurador al explorador para habilitar la depuración de scripts del lado cliente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] utiliza el motor de depuración de scripts para este propósito. Para habilitar la depuración de scripts, debe cambiar la configuración predeterminada del explorador cuando se le solicite.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] asocia el depurador solo a los procesos W3WP o SPUCWorkerProcess que se ejecutan en el sitio actual. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] también adjunta los motores de depuración de flujo de trabajo y COM administrados.

## <a name="see-also"></a>Vea también
- [Depurar soluciones de SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Build and debug SharePoint solutions](../sharepoint/building-and-debugging-sharepoint-solutions.md) (Compilar y depurar las soluciones de SharePoint)
- [Consideraciones sobre las soluciones de espacio aislado](../sharepoint/sandboxed-solution-considerations.md)
