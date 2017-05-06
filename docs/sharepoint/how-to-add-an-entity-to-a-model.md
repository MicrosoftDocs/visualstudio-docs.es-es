---
title: "C&#243;mo: Agregar una entidad a un modelo"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EntityTool"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], agregar una entidad"
  - "BDC [desarrollo de SharePoint en Visual Studio], entidad"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], agregar una entidad"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], entidad"
ms.assetid: 139a6639-dabe-4e14-bb64-e5f4efb6f2fb
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# C&#243;mo: Agregar una entidad a un modelo
  Para crear una entidad, agregue un control de la entidad de Visual Studio **Cuadro de herramientas** sobre el diseñador de \(BDC\) de conectividad a datos profesionales.  
  
### Para agregar una entidad al modelo  
  
1.  Cree un nuevo proyecto BDC o abra uno existente.  Para obtener más información, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
2.  En **Cuadro de herramientas**, el grupo de **BusinessDataCatalog** , agregue un control de **Entidad** sobre el diseñador.  
  
     La nueva entidad aparece en el diseñador.  Visual Studio agrega un elemento `<Entity>` al XML del archivo del modelo BDC en su proyecto.  Para obtener más información sobre los atributos de un elemento de entidad, vea. [Entidad](http://go.microsoft.com/fwlink/?LinkId=169296)  
  
3.  En el diseñador, abra el menú contextual para la entidad, elija **Add**y, a continuación **Identificador**.  
  
     Un nuevo identificador aparece en la entidad.  
  
    > [!NOTE]  
    >  Se puede cambiar el nombre de la entidad y del identificador en la ventana **Propiedades**.  
  
4.  Defina los campos de la entidad en una clase.  Puede agregar una nueva clase al proyecto o usar una clase existente creada a través de otras herramientas, como Object Relational Designer.  En el siguiente ejemplo se muestra una clase de entidad denominada Contact.  
  
     [!code-csharp[SP_BDC_Entity_Data_Class#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/cs/bdcmodel1/contact.cs#1)]
     [!code-vb[SP_BDC_Entity_Data_Class#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc_entity_data_class/vb/bdcmodel1/contact.vb#1)]  
  
## Vea también  
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)  
  
  