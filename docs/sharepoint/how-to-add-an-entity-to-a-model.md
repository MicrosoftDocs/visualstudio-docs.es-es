---
title: Procedimiento Agregar una entidad a un modelo | Documentos de Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- EntityTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b269bb18580784fb08d9b081a37935c7b3f37627
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "54864668"
---
# <a name="how-to-add-an-entity-to-a-model"></a>Procedimiento Agregar una entidad a un modelo
  Para crear una entidad, agregue un control de la entidad desde Visual Studio **cuadro de herramientas** hasta el Diseñador de conectividad de datos profesionales (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Para agregar una entidad al modelo  
  
1.  Crear un proyecto BDC o abra un proyecto existente de BDC. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  En el **cuadro de herramientas**, desde el **BusinessDataCatalog** de grupo, agregue un **entidad** control en el diseñador.  
  
     La nueva entidad aparece en el diseñador. Visual Studio agrega un `<Entity>` elemento al XML del archivo de modelo BDC en su proyecto. Para obtener más información acerca de los atributos de un elemento de entidad, vea [entidad](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  En el diseñador, abra el menú contextual de la entidad, elija **agregar**y, a continuación, elija **identificador**.  
  
     Un nuevo identificador aparece en la entidad.  
  
    > [!NOTE]  
    >  Puede cambiar el nombre de la entidad y el identificador de la **propiedades** ventana.  
  
4.  Defina los campos de la entidad en una clase. Puede agregar una nueva clase al proyecto o utilizar una clase existente creada mediante otras herramientas como el Object Relational Designer (Object Relational Designer). El ejemplo siguiente muestra una clase de entidad con el nombre de contacto.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Vea también
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)  
