---
title: "C&#243;mo: Crear asociaciones de archivo para una aplicaci&#243;n ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "implementación ClickOnce, asociaciones de archivos"
  - "asociaciones de archivos, aplicaciones ClickOnce"
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Crear asociaciones de archivo para una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las aplicaciones [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pueden estar asociadas a una o varias extensiones de nombre de archivo, de modo que se iniciarán automáticamente cuando el usuario abra un archivo de estos tipos.  Resulta sencillo agregar a una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] la compatibilidad con las extensiones de nombre de archivo.  
  
### Para crear asociaciones de archivos en una aplicación ClickOnce  
  
1.  Cree una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o utilice una aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] existente.  
  
2.  Abra el manifiesto de aplicación con un editor de texto o un editor XML, como Bloc de notas.  
  
3.  Busque el elemento `assembly`.  Para obtener más información, vea [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Agregue un elemento `fileAssociation` como elemento secundario de `assembly`.  El elemento `fileAssociation` tiene cuatro atributos.  
  
    -   `extension`: extensión de nombre de archivo que desea asociar a la aplicación.  
  
    -   `description`: descripción del tipo de archivo, que aparecerá en el shell de Windows.  
  
    -   `progid`: cadena que identifica de forma inequívoca el tipo de archivo para marcarlo en el Registro.  
  
    -   `defaultIcon`: icono que se va a utilizar en este tipo de archivo.  El icono debe agregarse como un recurso de archivo en el manifiesto de aplicación.  Para obtener más información, vea [Cómo: Incluir un archivo de datos en una aplicación ClickOnce](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Para obtener un ejemplo de los elementos `file` y `fileAssociation`, vea [\<fileAssociation\> \(Elemento\)](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Si desea asociar varios tipos de archivo a la aplicación, agregue otros elementos `fileAssociation`.  Tenga en cuenta que el atributo `progid` debería ser diferente en cada uno de ellos.  
  
6.  Cuando termine de trabajar con el manifiesto de aplicación, fírmelo de nuevo.  Puede hacerlo desde la línea de comandos mediante Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Para obtener más información, vea [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md).  
  
## Vea también  
 [\<fileAssociation\> \(Elemento\)](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifiesto de aplicación ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe \(Herramienta de generación y edición de manifiestos\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)