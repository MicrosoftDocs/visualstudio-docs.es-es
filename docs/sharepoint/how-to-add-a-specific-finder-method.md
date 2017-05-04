---
title: "C&#243;mo: Agregar un m&#233;todo Finder espec&#237;fico | Microsoft Docs"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], obtener una entidad"
  - "BDC [desarrollo de SharePoint en Visual Studio], devolver una entidad"
  - "BDC [desarrollo de SharePoint en Visual Studio], método Finder específico"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], obtener una entidad"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], devolver una entidad"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], método Finder específico"
ms.assetid: 7bbc5986-2828-4755-96fa-9f1dc0f8dc75
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# C&#243;mo: Agregar un m&#233;todo Finder espec&#237;fico
  Puede devolver una instancia de entidad única creando un método *Finder específico*.  El servicio de \(BDC\) de conectividad a datos profesionales ejecuta el método Finder específico cuando un usuario elige una entidad en una lista web del elemento o externa de datos profesionales.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Para crear un método Finder específico  
  
1.  En el diseñador de BDC, elija una entidad.  
  
     Para obtener información sobre cómo agregar una entidad al diseñador de BDC en Visual Studio, vea [Cómo: Agregar una entidad a un modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
2.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
     Se abre la ventana **Detalles del método de BDC**.  Para obtener más información sobre la ventana, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En la lista de **Agregar un método** , elija **Crear método Finder específico**.  
  
     Visual Studio agrega los siguientes elementos al modelo.  Estos elementos aparecen en la ventana **Detalles del método de BDC**.  
  
    -   Un método  
  
    -   Un parámetro de entrada para el método.  
  
    -   Un parámetro devuelto para el método.  
  
    -   Un descriptor de tipo para cada parámetro.  
  
    -   Una instancia de método para el método.  
  
     Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  Abra la ventana **Propiedades** de Visual Studio.  
  
5.  Configure el descriptor de tipos del parámetro devuelto como un descriptor de tipos de entidades.  Para obtener información sobre cómo crear un descriptor de tipo de entidad, vea [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
    > [!NOTE]  
    >  No tiene que seguir este paso si ha agregado un método Finder a la entidad.  Visual Studio utiliza el descriptor de tipos que definió en el método Finder.  
  
    > [!NOTE]  
    >  Si el campo de identificador del tipo de entidad representa un campo de una tabla de base de datos que se genera automáticamente, establezca la propiedad de **sólo lectura** del campo de identificador en **VERDADERO**.  
  
6.  En la ventana de **Detalles del método** , elija la instancia de método del método.  
  
7.  En la **ventana Propiedades**, establezca la propiedad **Nombre del parámetro de devolución** en el nombre del parámetro devuelto del método.  Para obtener más información sobre las propiedades de la instancia de método, vea [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
8.  En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio generado para la entidad y, a continuación **Ver código**.  
  
     El archivo de código del servicio de entidad se abre en el editor de código.  Para obtener más información sobre el archivo de código del servicio de entidad, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
9. Agregue código al método Finder específico.  Este código realiza las tareas siguientes:  
  
    -   Recupera un registro de un origen de datos.  
  
    -   Devuelve una entidad al servicio BDC.  
  
     En el siguiente ejemplo se devuelve un contacto de la base de datos de ejemplo AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Vea también  
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  