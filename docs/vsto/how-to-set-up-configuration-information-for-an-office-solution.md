---
title: "C&#243;mo: Establecer la informaci&#243;n de configuraci&#243;n para una soluci&#243;n de Office | Microsoft Docs"
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
helpviewer_keywords: 
  - "archivos de configuración [desarrollo de Office en Visual Studio]"
  - "soluciones [desarrollo de Office en Visual Studio], archivos de configuración"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# C&#243;mo: Establecer la informaci&#243;n de configuraci&#243;n para una soluci&#243;n de Office
  Es posible usar archivos de configuración para establecer los valores que son específicos de las soluciones de Office.  Se pueden especificar valores de configuración como directivas de enlace de los ensamblados, objetos de comunicación remota, depuración y seguimiento.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Para agregar un archivo de configuración al proyecto de Office  
  
1.  En el menú **Proyecto**, haga clic en **Agregar nuevo elemento**.  
  
2.  En el panel **Categorías**, haga clic en **General**.  
  
3.  En el panel **Plantillas**, seleccione **Archivo de configuración de aplicaciones** .  
  
4.  En el cuadro **Nombre**, escriba el mismo nombre que tiene el ensamblado, con la extensión .config.  Por ejemplo, un archivo de configuración correspondiente un ensamblado de un proyecto de Excel llamado ExcelWorkbook1.dll se llamaría ExcelWorkbook1.dll.config.  
  
5.  Haga clic en **Agregar**.  
  
6.  Cree su archivo de configuración de acuerdo con el esquema del archivo de configuración de la aplicación.  Para obtener más información, vea [Esquema de los archivos de configuración de .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38).  
  
 No hay ninguna consideración especial para usar archivos de configuración con proyectos de Office.  
  
## Vea también  
 [Esquema de los archivos de configuración de .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)  
  
  