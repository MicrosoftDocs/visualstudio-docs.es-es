---
title: "C&#243;mo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios"
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
  - "desarrollo de aplicaciones [desarrollo de Office en Visual Studio], automatización"
  - "ensamblados [desarrollo de Office en Visual Studio], Referencias PIA"
  - "aplicaciones de Office [desarrollo de Office en Visual Studio], automatización"
  - "ensamblados de interoperabilidad primarios de Office en Visual Studio, agregar referencias"
  - "ensamblados de interoperabilidad primarios [desarrollo de Office en Visual Studio], agregar referencias"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# C&#243;mo: Apuntar a las aplicaciones de Office mediante los ensamblados de interoperabilidad primarios
  Cuando se crea un nuevo proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados de interoperabilidad primarios \(PIA\) de Microsoft Office necesarios para compilar el proyecto.  Debe agregar referencias a otros PIA en los escenarios siguientes:  
  
-   Desea usar las características de otras aplicaciones de Microsoft Office en su proyecto.  Por ejemplo, quizás le interese usar las características de Microsoft Office Excel en un proyecto de Microsoft Office Word.  
  
-   Desea automatizar las aplicaciones de Microsoft Office que no tienen proyectos dedicados en Visual Studio, como Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Para agregar una referencia a un ensamblado de interoperabilidad primario  
  
1.  Abra el proyecto de Office y seleccione el nombre del proyecto en el **Explorador de soluciones**.  
  
2.  En el menú **Proyecto**, haga clic en **Agregar referencia**.  
  
3.  En la pestaña **.NET Framework**, seleccione el PIA que desee en la lista **Nombre de componente**.  Para obtener más información sobre los ensamblados de interoperabilidad primarios de Microsoft Office disponibles, consulte [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
     Si el proyecto tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versiones posteriores, la propiedad **Incrustar tipos de interoperabilidad** para la referencia de ensamblado está establecida en **True** de forma predeterminada.  Con esta configuración, la solución no requiere el PIA en los equipos de los usuarios finales.  Para obtener más información, consulte el artículo sobre [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  En proyectos de Office, agregue siempre referencias a los PIA de Office mediante la pestaña **.NET** del cuadro de diálogo **Agregar referencia**, en lugar de usar la pestaña **COM**.  Para obtener más información, consulte [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Haga clic en **Aceptar**.  
  
     El nombre del ensamblado aparece en la carpeta **Referencias** del **Explorador de soluciones**.  
  
## Vea también  
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  