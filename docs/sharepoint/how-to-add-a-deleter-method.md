---
title: "C&#243;mo: Agregar un m&#233;todo Deleter | Microsoft Docs"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], Deleter"
  - "BDC [desarrollo de SharePoint en Visual Studio], eliminar datos"
  - "BDC [desarrollo de SharePoint en Visual Studio], eliminar instancias de entidad"
  - "BDC [desarrollo de SharePoint en Visual Studio], quitar datos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], Deleter"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], eliminar datos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], eliminar instancias de entidad"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], quitar datos"
ms.assetid: 3362eaf4-5dc7-4450-9009-b296308ae61f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# C&#243;mo: Agregar un m&#233;todo Deleter
  Puede permitir a un usuario final eliminar un registro de datos de una lista externa de un sitio de SharePoint agregando un método *Deleter* al modelo.  Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Para crear un método Deleter  
  
1.  En el diseñador de BDC, elija una entidad.  
  
2.  En la barra de menú, elija **Visualización**, **Otras ventanas**, **Detalles del método de BDC**.  
  
     Se abre la ventana **Detalles del método de BDC**.  Para obtener más información sobre esta ventana, vea [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md).  
  
3.  En la lista de **Agregar un método** , elija **Cree un método Deleter**.  
  
     Visual Studio agrega los siguientes elementos al modelo.  Estos elementos aparecen en la ventana **Detalles del método de BDC**.  
  
    -   Un método denominado **Delete**.  
  
    -   Un parámetro de entrada para el método.  
  
    -   Un descriptor de tipos del parámetro.  
  
    -   Una instancia de método para el método.  
  
     Para obtener más información, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
4.  En **Explorador de soluciones**, abra el menú contextual del archivo de código de servicio generado para la entidad y, a continuación **Ver código**.  
  
     El archivo de código del servicio de entidad se abre en el editor de código.  Para obtener más información sobre el archivo de código del servicio de entidad, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
5.  Agregue código al método Deleter para eliminar un registro.  En el siguiente ejemplo se elimina un elemento de línea de un pedido de ventas utilizando la base de datos de ejemplo de AdventureWorks para SQL Server.  
  
    > [!NOTE]  
    >  El método de este ejemplo utiliza dos parámetros de entrada.  
  
    > [!NOTE]  
    >  Reemplace el valor del campo `ServerName` con el nombre del servidor.  
  
     [!code-csharp[SP_BDC#6](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#6)]
     [!code-vb[SP_BDC#6](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#6)]  
  
## Vea también  
 [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un método Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Cómo: Agregar un método Finder específico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Cómo: Agregar un método Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Cómo: Agregar un método Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Introducción general a las herramientas de diseño del modelo BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Cómo: Agregar un parámetro a un método](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Cómo: Definir la instancia de un método](../sharepoint/how-to-define-a-method-instance.md)  
  
  