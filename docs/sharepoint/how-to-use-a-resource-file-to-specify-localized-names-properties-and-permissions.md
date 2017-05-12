---
title: "C&#243;mo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados | Microsoft Docs"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], localizar cadenas"
  - "BDC [desarrollo de SharePoint en Visual Studio], propiedades"
  - "BDC [desarrollo de SharePoint en Visual Studio], archivo de recursos"
  - "BDC [desarrollo de SharePoint en Visual Studio], cadenas de recursos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], localizar cadenas"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], propiedades"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], archivo de recursos"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], cadenas de recursos"
ms.assetid: 72bb744d-818b-4e5a-9da2-295412025680
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# C&#243;mo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados
  Mediante un archivo de recursos, puede proporcionar nombres traducidos, definir propiedades, y aplicar los objetos de tor de los permisos que se definen en un modelo de \(BDC\) de conectividad a datos profesionales.  Para especificar esta información, se agrega un elemento de **Recurso de conectividad a datos profesionales** a un proyecto que contenga un elemento de **Modelo de conectividad a datos empresariales** .  A continuación se especifica nombres, propiedades y permisos XML del archivo de recursos.  
  
### Para agregar un archivo de recursos de BDC a un proyecto de SharePoint  
  
1.  En **Explorador de soluciones**, expanda la carpeta para el proyecto de SharePoint y, a continuación la carpeta que contiene el modelo BDC.  
  
2.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
3.  Expanda el nodo de **sharepoint** y, a continuación el nodo de **2010** .  
  
4.  En el cuadro de diálogo de **Agregar nuevo elemento** , elija **Elemento de recurso de conectividad a datos profesionales**.  
  
5.  En el cuadro de **Name** , especifique el nombre del archivo de recursos, y elija el botón de **Add** .  
  
     Un archivo de recursos que tiene la extensión .bdcr se agrega al proyecto y se abrirá para editar.  
  
6.  Agregue XML para definir los nombres, las propiedades, y los permisos traducidos que desea aplicar el modelo BDC.  
  
     Para obtener información sobre cómo definir estos elementos, vea [Modelo y archivos de recursos](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## Vea también  
 [Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  