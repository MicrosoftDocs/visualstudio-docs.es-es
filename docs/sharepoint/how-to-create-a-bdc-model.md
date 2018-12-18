---
title: 'Cómo: crear un modelo BDC | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1a0e2bc47c902707ee896c46fa0d9988551fa6fd
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757927"
---
# <a name="how-to-create-a-bdc-model"></a>Cómo: crear un modelo BDC
  Puede crear un modelo de conectividad de datos profesionales (BDC) mediante la plantilla para ese tipo de elemento y, a continuación, agregar el modelo a un proyecto de SharePoint. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md). Para obtener más información sobre cómo diseñar el modelo, vea [diseñar un modelo de conectividad a datos empresariales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Para crear un proyecto BDC  
  
1.  En la barra de menús, elija **Archivo** > **Nuevo** > **Proyecto**.  
  
    > [!NOTE]  
    >  Si el IDE está establecido para usar la configuración de desarrollo de Visual Basic, elija **archivo** > **nuevo proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
2.  Bajo **Visual Basic** o **Visual C#**, elija **Office/SharePoint**, **soluciones de SharePoint**.  
  
3.  En el **plantillas** panel, elija el **SharePoint 2013 - proyecto vacío** elemento y, a continuación, elija el **Aceptar** botón.  
  
     El **Asistente de personalización de SharePoint** se abre.  
  
4.  En el **especificar el nivel de sitio y de seguridad para la depuración** página, especifique la dirección URL de un sitio de SharePoint en el equipo local, elija el **implementar como solución de granja de servidores** botón de opción y, a continuación, elija el **Finalizar** botón.  
  
     Probará el modelo en el sitio de SharePoint que ha especificado.  
  
    > [!IMPORTANT]  
    >  Debe implementar el proyecto como una solución de granja porque los modelos BDC admiten solo las soluciones de granja de servidores.  
  
     Se crea un proyecto de SharePoint vacío.  
  
5.  En la barra de menús, elija **Proyecto** >  **Agregar nuevo elemento**.  
  
6.  En el **Agregar nuevo elemento** diálogo cuadro, elija el **Office/SharePoint** nodo.  
  
7.  En la lista de plantillas de SharePoint, elija **(solución de granja de servidores únicamente) modelo de conectividad a datos empresariales**.  
  
8.  En el **nombre** cuadro, especifique un nombre para el modelo BDC y, a continuación, elija el **agregar** botón.  
  
     Un **modelo de conectividad a datos empresariales** elemento se agrega al proyecto. De forma predeterminada, el modelo aparece en el diseñador BDC. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>Vea también
 [Crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Cómo: usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrar datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
