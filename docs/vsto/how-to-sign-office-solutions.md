---
title: "C&#243;mo: Firmar soluciones de Office | Microsoft Docs"
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
  - "certificados [desarrollo de Office en Visual Studio], soluciones de Office"
  - "seguridad [desarrollo de Office en Visual Studio], firmar soluciones de Office"
  - "firmar manifiestos [desarrollo de Office en Visual Studio]"
ms.assetid: d3df5ee6-f1b7-47ed-b7ee-8985679ee3af
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: Firmar soluciones de Office
  Si firma una solución, puede otorgar plena confianza a la solución utilizando el certificado como prueba.  Puede utilizar el mismo certificado para varias soluciones y todas las soluciones serán de confianza sin necesidad de actualizaciones adicionales de la directiva de seguridad.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Si modifica manualmente los manifiestos de aplicación e implementación utilizando la herramienta de generación y edición de manifiestos \(mage.exe y mageui.exe\), debe volver a firmar los manifiestos antes de poder utilizarlos.  Para obtener más información, vea [Cómo: Volver a firmar manifiestos de aplicación e implementación](../Topic/How%20to:%20Re-sign%20Application%20and%20Deployment%20Manifests.md).  
  
## Firmar mediante un certificado  
 Un certificado es un archivo que contiene una clave única y la identidad del editor de la solución.  Puede adquirir certificados de una entidad de certificación o crear su propio certificado y hacer que una entidad de certificación lo firme.  
  
 Visual Studio firma soluciones de Office con un certificado temporal para habilitar la depuración.  No debe utilizar el certificado temporal en soluciones implementadas como prueba.  
  
#### Para firmar una solución de Office mediante un certificado  
  
1.  En el menú **Proyecto**, haga clic en **Propiedades de** *nombreDeSolución*.  
  
2.  Haga clic en la ficha **Firma**.  
  
3.  Seleccione **Firmar los manifiestos de ClickOnce**.  
  
4.  Busque el certificado haciendo clic en **Seleccionar del almacén** o en **Seleccionar del archivo** y navegando al certificado.  
  
5.  Para comprobar que se utiliza el certificado correcto, haga clic en **Más detalles** para ver la información del certificado.  
  
## Vea también  
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Otorgar confianza a las soluciones de Office](../vsto/granting-trust-to-office-solutions.md)   
 [Página Firma, Diseñador de proyectos](../ide/reference/signing-page-project-designer.md)  
  
  