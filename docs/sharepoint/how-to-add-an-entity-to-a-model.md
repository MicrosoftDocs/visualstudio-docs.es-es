---
title: "Cómo: agregar una entidad a un modelo | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: EntityTool
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], entity
- Business Data Connectivity service [SharePoint development in Visual Studio], adding an entity
- Business Data Connectivity service [SharePoint development in Visual Studio], entity
- BDC [SharePoint development in Visual Studio], adding an entity
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: ec34a6f93625fdb2cb8a1e5fcc5fb5c95d17653b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-entity-to-a-model"></a>Cómo: Agregar una entidad a un modelo
  Para crear una entidad, agregue un control de entidad desde Visual Studio **cuadro de herramientas** en el Diseñador de conectividad de datos profesionales (BDC).  
  
### <a name="to-add-an-entity-to-the-model"></a>Para agregar una entidad al modelo  
  
1.  Crear un proyecto BDC o abrir un proyecto existente de BDC. Para obtener más información, consulte [crear un modelo de conectividad a datos empresariales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  En el **cuadro de herramientas**, desde el **BusinessDataCatalog** grupo, agregue un **entidad** control en el diseñador.  
  
     La nueva entidad aparece en el diseñador. Visual Studio agrega un `<Entity>` elemento en el XML del archivo de modelo BDC en su proyecto. Para obtener más información acerca de los atributos de un elemento de entidad, vea [entidad](http://go.microsoft.com/fwlink/?LinkId=169296).  
  
3.  En el diseñador, abra el menú contextual de la entidad, elija **agregar**y, a continuación, elija **identificador**.  
  
     Un nuevo identificador aparece en la entidad.  
  
    > [!NOTE]  
    >  Puede cambiar el nombre de la entidad y el identificador de la **propiedades** ventana.  
  
4.  Define los campos de la entidad en una clase. Puede agregar una nueva clase al proyecto o utilizar una clase existente que se crea mediante otras herramientas como el Object Relational Designer (Object Relational Designer). En el ejemplo siguiente se muestra una clase de entidad con el nombre de contacto.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/CSharp/sp_bdc_entity_data_class/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../sharepoint/codesnippet/VisualBasic/sp_bdc_entity_data_class/bdcmodel1/contact.vb#1)]  
  
## <a name="see-also"></a>Vea también  
 [Cómo: agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  