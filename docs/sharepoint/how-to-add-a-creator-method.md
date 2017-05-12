---
title: "C&#243;mo: Agregar un m&#233;todo Creator"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], agregar entidades"
  - "BDC [desarrollo de SharePoint en Visual Studio], agregar instancias de entidad"
  - "BDC [desarrollo de SharePoint en Visual Studio], Creator"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], agregar entidades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], agregar instancias de entidad"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], Creator"
ms.assetid: 52f0382f-10a0-4a51-83fe-6f22f4647df8
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# C&#243;mo: Agregar un m&#233;todo Creator
  Un método Creator agrega nuevos datos al origen de datos de una entidad.  Las llamadas al servicio de \(BDC\) de conectividad a datos profesionales este método cuando los usuarios elija el botón de **Nuevo elemento** en la cinta de opciones de una lista basada en el modelo.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Para agregar un método Creator  
  
1.  En el diseñador de BDC, elija una entidad.  
  
2.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
     Se abre la ventana **Detalles del método de BDC**.  Para obtener más información sobre la ventana, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En la lista de **Agregar un método** , elija **Crear método Creator**.  
  
     Visual Studio agrega los siguientes elementos al modelo, y estos elementos aparecen en la ventana de **Detalles del método de BDC** .  
  
    -   Un método denominado **Create**.  
  
    -   Un parámetro de entrada para el método.  
  
    -   Un parámetro devuelto para el método.  
  
    -   Descriptores de tipos para los parámetros.  
  
    -   Una instancia de método para el método.  
  
     Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio generado para la entidad y, a continuación **Ver código**.  
  
     El archivo de código del servicio de entidad se abre en el editor de código.  Para obtener más información sobre el archivo de código del servicio de entidad, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Agregue el código al método Creator que agrega nuevos datos a un origen de datos.  El ejemplo siguiente se agrega un contacto a la base de datos de ejemplo AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#4](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#4)]
     [!code-vb[SP_BDC#4](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#4)]  
  
## Vea también  
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  