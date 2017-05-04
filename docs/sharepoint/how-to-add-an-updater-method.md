---
title: "C&#243;mo: Agregar un m&#233;todo Updater | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], Updater"
  - "BDC [desarrollo de SharePoint en Visual Studio], actualizar datos"
  - "BDC [desarrollo de SharePoint en Visual Studio], actualizar instancias de entidad"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], Updater"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], actualizar datos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], actualizar instancias de entidad"
ms.assetid: c97e443c-58dc-4f8f-8cbd-0d52d8a6a06b
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# C&#243;mo: Agregar un m&#233;todo Updater
  Puede permitir a los usuarios actualizar datos empresariales en una lista externa de SharePoint creando un método *Updater*.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Para crear un método Updater  
  
1.  En el diseñador de BDC, elija una entidad.  
  
2.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
     Se abre la ventana Detalles del método de BDC.  Para obtener más información sobre esta ventana, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En la lista de **Agregar un método** , elija **Crear método Updater**.  
  
     Visual Studio agrega los siguientes elementos al modelo.  Estos elementos aparecen en la ventana Detalles del método de BDC.  
  
    -   Un método denominado **Actualización**.  
  
    -   Un parámetro de entrada para el método.  
  
    -   Un descriptor de tipos del parámetro.  De forma predeterminada, Visual Studio usa el descriptor de tipo de entidad que definió para el método Finder \(por ejemplo: Contacto\).  
  
    -   Una instancia de método para el método.  
  
     Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
    > [!NOTE]  
    >  Si el identificador del tipo de entidad representa un campo de una tabla de base de datos que no se ha generado automáticamente, establezca la propiedad de **Campo Pre\-Updater** a **VERDADERO**.  
  
4.  En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio generado para la entidad y, a continuación **Ver código**.  
  
     El archivo de código del servicio de entidad se abre en el editor de código.  Para obtener más información sobre este archivo, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Agregue código al método update a los datos.  En el siguiente ejemplo se actualiza la información de un contacto de la base de datos de ejemplo AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#5](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#5)]
     [!code-vb[SP_BDC#5](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#5)]  
  
## Vea también  
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [How to: Add an Updater Method](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  