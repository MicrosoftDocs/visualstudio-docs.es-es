---
title: Procedimiento Editar una configuración de implementación de SharePoint | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ffa7923bbe7e8a7b44fec280a5528ab023feed37
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444698"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Procedimiento Editar una configuración de implementación de SharePoint
  Puede crear una configuración de implementación o modificar una configuración de implementación existente. Por ejemplo, podría ejecutar un paso único o cambiar el orden de los pasos del proceso de implementación. Es posible que desee crear o modificar las configuraciones de implementación porque no se puede cambiar las configuraciones integradas y se ha agregado mediante programación.

## <a name="create-a-sharepoint-deployment-configuration"></a>Crear una configuración de implementación de SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Para crear una configuración de implementación de SharePoint

1. En **el Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto**, _ProjectName_**propiedades**.

2. En el **SharePoint** ficha, elija la **New** botón.

     El **agregar nueva configuración de implementación** aparece el cuadro de diálogo.

3. En el **nombre** texto, escriba un nombre para la configuración de implementación.

4. En el **pasos de implementación disponibles** panel, elija los pasos que desea agregar a la configuración de implementación, elija el (**>**) botón y, a continuación, elija el **Aceptar** botón.

    > [!NOTE]
    > Si ha configurado un comando anterior a la implementación o un comando posterior a la implementación, estos pasos se ejecutan sólo si se agregan a una configuración de implementación personalizado.

## <a name="change-the-active-deployment-configuration"></a>Cambiar la configuración de implementación activa

#### <a name="to-change-the-active-deployment-configuration"></a>Para cambiar la configuración de implementación activa

1. En **el Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto** > **\<*ProjectName*> Propiedades**.

2. Elija la **SharePoint** ficha.

3. En el **Active Deployment Configuration** cuadro de lista, elija el nombre de la configuración de implementación que desea usar.

## <a name="see-also"></a>Vea también
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
