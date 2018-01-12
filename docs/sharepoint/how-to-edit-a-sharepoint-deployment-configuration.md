---
title: "Cómo: editar una configuración de implementación de SharePoint | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4e5e65e82910239b596e4b19f2ea1fa1f357266c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Cómo: Modificar una configuración de implementación de SharePoint
  Puede crear una configuración de implementación o modificar una configuración de implementación existente. Por ejemplo, podría ejecutar un paso único o cambiar el orden de los pasos del proceso de implementación. Puede que desee crear o modificar las configuraciones de implementación porque no se puede cambiar las configuraciones integradas y agregadas mediante programación.  
  
## <a name="creating-a-sharepoint-deployment-configuration"></a>Crear una configuración de implementación de SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Para crear una configuración de implementación de SharePoint  
  
1.  En **el Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto**, *ProjectName***propiedades**.  
  
2.  En el **SharePoint** ficha, elija la **New** botón.  
  
     El **agregar nueva configuración de implementación** aparece el cuadro de diálogo.  
  
3.  En el **nombre** texto cuadro, escriba un nombre para la configuración de implementación.  
  
4.  En el **pasos de implementación disponibles** panel, elija los pasos que desea agregar a la configuración de implementación, elija el (**>**) botón y, a continuación, elija el **Aceptar** botón.  
  
    > [!NOTE]  
    >  Si ha configurado un comando anterior a la implementación o un comando posterior a la implementación, ejecutan estos pasos únicamente si se agregan a una configuración de implementación personalizada.  
  
## <a name="changing-the-active-deployment-configuration"></a>Cambiar la configuración de implementación activa  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Para cambiar la configuración de implementación activa  
  
1.  En **el Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto**, *ProjectName***propiedades**.  
  
2.  Elija la **SharePoint** ficha.  
  
3.  En el **Active Deployment Configuration** cuadro de lista, elija el nombre de la configuración de implementación que desea usar.  
  
## <a name="see-also"></a>Vea también  
 [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  