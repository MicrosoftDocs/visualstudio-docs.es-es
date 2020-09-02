---
title: 'Cómo: editar una configuración de implementación de SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 74f6377bad0f62aa2c470e72afe64b85b3017ee6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016785"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Cómo: editar una configuración de implementación de SharePoint
  Puede crear una configuración de implementación o modificar una configuración de implementación existente. Por ejemplo, puede ejecutar un solo paso o cambiar el orden de los pasos en el proceso de implementación. Puede que desee crear o modificar configuraciones de implementación porque las configuraciones integradas y agregadas mediante programación no se pueden cambiar.

## <a name="create-a-sharepoint-deployment-configuration"></a>Crear una configuración de implementación de SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Para crear una configuración de implementación de SharePoint

1. En **Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de menús, elija **proyecto**,**propiedades**de _projectname_.

2. En la pestaña **SharePoint** , elija el botón **nuevo** .

     Aparecerá el cuadro de diálogo **Agregar nueva configuración de implementación** .

3. En el cuadro de texto **nombre** , escriba un nombre para la configuración de implementación.

4. En el panel **pasos de implementación disponibles** , elija los pasos que quiere agregar a la configuración de implementación, elija el **>** botón () y, a continuación, elija el botón **Aceptar** .

    > [!NOTE]
    > Si ha configurado un comando anterior a la implementación o un comando posterior a la implementación, estos pasos solo se ejecutan si los agrega a una configuración de implementación personalizada.

## <a name="change-the-active-deployment-configuration"></a>Cambiar la configuración de implementación activa

#### <a name="to-change-the-active-deployment-configuration"></a>Para cambiar la configuración de implementación activa

1. En **Explorador de soluciones**, elija un proyecto de SharePoint y, a continuación, en la barra de **Project** menús, elija  >  ** \<*ProjectName*> propiedades**del proyecto.

2. Elija la pestaña **SharePoint** .

3. En el cuadro de lista **configuración de implementación activa** , elija el nombre de la configuración de implementación que desee usar.

## <a name="see-also"></a>Consulte también
- [Empaquetar e implementar soluciones de SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
