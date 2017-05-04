---
title: "C&#243;mo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint | Microsoft Docs"
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
  - "VS.SharePointTools.BDC.ImportDialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], importar un modelo"
  - "BDC [desarrollo de SharePoint en Visual Studio], quitar un modelo"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], importar un modelo"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], reutilizar un modelo"
ms.assetid: e843738a-f936-4dcd-be35-249407573b74
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint
  Puede personalizar, paquete, e implementar de nuevo un modelo de \(BDC\) de conectividad a datos profesionales mediante Visual Studio para agregar el archivo modelo \(.bdcm\) a cualquier proyecto de la granja de servidores de SharePoint.  Para obtener más información, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### Para agregar un modelo BDC en un proyecto de SharePoint  
  
1.  En **Explorador de soluciones**, elija la carpeta para un proyecto de SharePoint.  
  
2.  En la barra de menú, elija **Project**, **Agregar elemento existente**.  
  
3.  En el cuadro de diálogo de **Agregar elemento existente** , vaya a la ubicación del archivo de definición del modelo que desea agregar al proyecto, elija el archivo, y después elija el botón de **Add** .  
  
     Si el modelo no define *un sistema de \(LOB\) de línea de negocio del tipo ensamblado de .NET*, el cuadro de diálogo **Agregar LobSystem de ensamblado .NET** abra.  
  
4.  Si aparece el cuadro de diálogo, realice uno de los pasos siguientes:  
  
    -   Si desea escribir código personalizado y utilizar un diseñador para definir los metadatos del modelo importado, elija el botón de **Sí** , llame al sistema, y elija el botón de **Aceptar** .  
  
    -   Si no, elija el botón de **No** , y elija el botón de **Aceptar** .  
  
     El elemento **Modelo de conectividad a datos profesionales** se agrega al proyecto.  
  
## Vea también  
 [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  