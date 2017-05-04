---
title: "C&#243;mo: Agregar un m&#233;todo Finder | Microsoft Docs"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], Finder (método)"
  - "BDC [desarrollo de SharePoint en Visual Studio], obtener entidades"
  - "BDC [desarrollo de SharePoint en Visual Studio], devolver entidades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], Finder (método)"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], obtener entidades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], devolver entidades"
ms.assetid: 5de2cae3-d1f7-4a68-aac0-458967aca692
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# C&#243;mo: Agregar un m&#233;todo Finder
  Para habilitar el servicio conectividad a datos profesionales para mostrar una lista de entidades en un elemento web o lista, debe crear un método *Finder* .  Un método Finder es un método especial que devuelve una colección de instancias de entidad.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Para crear un método Finder  
  
1.  En el diseñador de BDC, elija una entidad.  
  
     Para obtener más información, vea [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
     Se abre la ventana **Detalles del método de BDC**.  Para obtener más información sobre la ventana **Detalles del método de BDC**, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En la lista de **Agregar un método** , elija **Crear método Finder**.  
  
     Visual Studio agrega un método, un parámetro devuelto y un descriptor de tipos.  
  
4.  Configure el descriptor de tipos como un descriptor de tipos de colección de entidades.  Para obtener más información sobre cómo crear un descriptor de tipos de colección de entidades, vea [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  No tiene que seguir este paso si ha agregado un método Finder específico a la entidad.  Visual Studio utiliza el descriptor de tipos que definió en el método Finder específico.  
  
5.  En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio generado para la entidad y, a continuación **Ver código**.  Para obtener más información sobre el archivo de código del servicio, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
6.  Agregue código al método Finder.  Este código realiza las tareas siguientes:  
  
    -   Recupera datos de un origen de datos.  
  
    -   Devuelve una lista de entidades al servicio BDC.  
  
     En el siguiente ejemplo se devuelve una colección de entidades `Contact` utilizando los datos de la base de datos de ejemplo AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Vea también  
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  