---
title: "C&#243;mo: Incluir un archivo de datos en una aplicaci&#243;n ClickOnce | Microsoft Docs"
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
  - "implementación ClickOnce, datos"
  - "acceso a datos, aplicaciones ClickOnce"
  - "implementar aplicaciones [ClickOnce], archivos de datos"
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# C&#243;mo: Incluir un archivo de datos en una aplicaci&#243;n ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

A cada aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que se instala se le asigna un directorio de datos en el disco local del equipo de destino donde la aplicación puede administrar sus propios datos.  Los archivos de datos pueden incluir archivos de cualquier tipo: archivos de texto, archivos XML o incluso archivos de base de datos de Microsoft Access \(.mdb\).  En los siguientes procedimientos se muestra cómo agregar un archivo de datos de cualquier tipo en la aplicación [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
### Para incluir un archivo de datos mediante Mage.exe  
  
1.  Agregue el archivo de datos al directorio de la aplicación junto con el resto de los archivos de la aplicación.  
  
     Normalmente, el directorio de la aplicación tendrá el nombre de la versión actual de la implementación, por ejemplo, v1.0.0.0.  
  
2.  Actualice el manifiesto de aplicación para mostrar el archivo de datos.  
  
     **mage \-u v1.0.0.0\\Application.manifest \-FromDirectory v1.0.0.0**  
  
     Cuando se realiza esta tarea, vuelve a crearse la lista de archivos del manifiesto de aplicación y también se generan automáticamente las firmas hash.  
  
3.  Abra el manifiesto de aplicación utilizando el editor de texto o de XML que prefiera y busque el elemento `file` del archivo recientemente agregado.  
  
     Si ha agregado un archivo XML denominado `Data.xml`, el archivo tendrá un aspecto similar al del siguiente ejemplo de código.  
  
 `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Agregue el atributo `type` a este elemento y asígnele un valor de `data`.  
  
 `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
1.  Vuelva a firmar el manifiesto de aplicación utilizando su certificado o par de claves y, a continuación, vuelva a firmar el manifiesto de implementación.  
  
     Es necesario volver a firmar el manifiesto de implementación porque el hash del manifiesto de aplicación ha cambiado.  
  
     **mage \-s app manifest \-cf cert\_file \-pwd password**  
  
     **mage \-u deployment manifest \-appm app manifest**  
  
     **mage \-s deployment manifest \-cf certfile \-pwd password**  
  
### Para incluir un archivo de datos mediante MageUI.exe  
  
1.  Agregue el archivo de datos al directorio de la aplicación junto con el resto de los archivos de la aplicación.  
  
2.  Normalmente, el directorio de la aplicación tendrá el nombre de la versión actual de la implementación, por ejemplo, v1.0.0.0.  
  
3.  En el menú **Archivo**, haga clic en **Abrir** para abrir el manifiesto de aplicación.  
  
4.  Seleccione la ficha **Archivos**.  
  
5.  En el cuadro de texto de la parte superior de la ficha, especifique el directorio que contiene los archivos de la aplicación y, a continuación, haga clic en **Rellenar**.  
  
     El archivo de datos aparecerá en la cuadrícula.  
  
6.  Establezca el valor **Tipo de archivo** del archivo de datos en **Datos**.  
  
7.  Guarde el manifiesto de aplicación y, a continuación, vuelva a firmar el archivo.  
  
     MageUI.exe le pedirá que vuelva a firmar el archivo.  
  
8.  Vuelva a firmar manifiesto de implementación  
  
     Es necesario volver a firmar el manifiesto de implementación porque el hash del manifiesto de aplicación ha cambiado.  
  
## Vea también  
 [Obtener acceso local o remoto a los datos en aplicaciones ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)