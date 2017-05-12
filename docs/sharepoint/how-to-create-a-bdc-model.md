---
title: "C&#243;mo: Crear un modelo BDC"
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
  - "BDC [desarrollo de SharePoint en Visual Studio], crear un modelo"
  - "servicio de conectividad a datos profesionales [desarrollo de SharePoint en Visual Studio], crear un modelo"
ms.assetid: e8b888d4-a531-4d13-9ebf-efbbd33eebc6
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Crear un modelo BDC
  Puede crear un modelo de conectividad a datos profesionales \(BDC\) mediante la plantilla para ese tipo de elemento y a continuación de agregar el modelo a cualquier proyecto de SharePoint.  Para obtener más información, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  Para obtener más información sobre cómo diseñar el modelo, vea [Diseñar un modelo de conectividad a datos profesionales](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### Para crear un proyecto de BDC  
  
1.  En la barra de menús, elija **Archivo**, **Nuevo**, **Proyecto**.  
  
    > [!NOTE]  
    >  Si el IDE está establecido para utilizar la configuración de desarrollo de Visual Basic, elija **Archivo**, **Nuevo proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En **Visual Basic** o **Visual C\#**, elija **Office\/SharePoint**, **Soluciones de SharePoint**.  
  
3.  En el panel **Plantillas**, elija el elemento **SharePoint 2013 \- Proyecto vacío** y elija el botón **Aceptar**.  
  
     Se abrirá el **Asistente para la personalización de SharePoint**.  
  
4.  En la página **Especifique el sitio y el nivel de seguridad de la depuración**, especifique la dirección URL de un sitio de SharePoint en el equipo local, elija el botón de opción **Implementar como solución de granja de servidores** y elija el botón **Finalizar**.  
  
     Probará el modelo en el sitio de SharePoint especificado.  
  
    > [!IMPORTANT]  
    >  Debe implementar el proyecto como solución de granja porque los modelos BDC solo admiten soluciones de granja.  
  
     Se crea un proyecto vacío de SharePoint.  
  
5.  En la barra de menús, elija **Proyecto**, **Agregar nuevo elemento**.  
  
6.  En el cuadro de diálogo **Agregar nuevo elemento**, elija el nodo **Office\/SharePoint**.  
  
7.  En la lista de plantillas de SharePoint, elija **Modelo de conectividad a datos profesionales \(solo en una solución de granja de servidores\)**.  
  
8.  En el cuadro **Nombre**, especifique un nombre para el patrón BDC y, a continuación, elija el botón **Agregar**.  
  
     Un elemento **Patrón de conectividad a datos profesionales** se agrega al proyecto.  De forma predeterminada, el modelo aparece en el diseñador de BDC.  Para obtener más información, vea [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## Vea también  
 [Crea un modelo de conectividad a datos profesionales](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Cómo: Agregar un archivo de modelo BDC existente a un proyecto de SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Cómo: Usar un archivo de recursos para especificar nombres, propiedades y permisos localizados](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Cómo: Incluir un ensamblado personalizado en una característica de BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrar Datos profesionales en SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  