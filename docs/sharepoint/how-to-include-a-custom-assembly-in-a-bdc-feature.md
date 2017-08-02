---
title: "C&#243;mo: Incluir un ensamblado personalizado en una caracter&#237;stica de BDC"
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
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "BDC [desarrollo de SharePoint en Visual Studio], agregar referencia"
  - "BDC [desarrollo de SharePoint en Visual Studio], ensamblado personalizado"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], agregar referencia"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], ensamblado personalizado"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# C&#243;mo: Incluir un ensamblado personalizado en una caracter&#237;stica de BDC
  Un proyecto puede hacer referencia a los ensamblados de otros proyectos en la misma solución.  Sin embargo, estos ensamblados deben agregarse al archivo de características del proyecto mediante el cuadro de diálogo **Asignar a LobSystems ensamblados a los que se hace referencia**.  
  
### Para incluir un ensamblado personalizado en una característica de Conectividad a datos profesionales \(BDC\)  
  
1.  En **Explorador de soluciones**, elija la carpeta que contiene el modelo BDC.  
  
2.  En el menú **Ver**, haga clic en la **Ventana Propiedades**.  
  
3.  En la ventana de **Propiedades** , elija la propiedad de **Ensamblados** y, a continuación los puntos suspensivos \(![Elipse del Diseñador de ASP.NET Mobile](~/docs/sharepoint/media/mwellipsis.gif "Elipse del Diseñador de ASP.NET Mobile")\).  
  
     Aparecerá el cuadro de diálogo **Asignar a LobSystems ensamblados a los que se hace referencia**.  
  
4.  En la lista de **Seleccionar un ensamblado** , elija el ensamblado personalizado.  
  
    > [!NOTE]  
    >  Los ensamblados solo aparecerán en el cuadro de diálogo **Asignar a LobSystems ensamblados a los que se hace referencia** si ha agregado una referencia al proyecto que contiene el ensamblado.  Para obtener más información, vea [Cómo: Agregar o quitar referencias utilizando el cuadro de diálogo Agregar referencia](http://msdn.microsoft.com/es-es/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  En el grupo de **Propiedades de la referencia** , abra la lista que aparece en la propiedad de **Ámbito de LobSystem** , elija el sistema LOB de los métodos que utilizan el ensamblado personalizado, y después elija el botón de **Aceptar** .  
  
    > [!NOTE]  
    >  Para depurar el código del ensamblado personalizado, debe agregar el ensamblado al paquete de la solución.  Para obtener más información, vea [Cómo: Agregar y quitar ensamblados adicionales](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## Vea también  
 [Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: Crear un modelo BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  