---
title: "Informaci&#243;n general sobre la administraci&#243;n de permisos sobre la informaci&#243;n y las extensiones de c&#243;digo administrado"
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
  - "documentos [desarrollo de Office en Visual Studio], permisos restringidos"
  - "Information Rights Management [desarrollo de Office en Visual Studio]"
  - "IRM [desarrollo de Office en Visual Studio]"
  - "documentos de Office [desarrollo de Office en Visual Studio], permisos restringidos"
  - "administración de derechos [desarrollo de Office en Visual Studio]"
  - "libros [desarrollo de Office en Visual Studio], permisos restringidos"
ms.assetid: 9728f5fe-9122-48e7-b0a3-9f5e0a16164f
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Informaci&#243;n general sobre la administraci&#243;n de permisos sobre la informaci&#243;n y las extensiones de c&#243;digo administrado
  Microsoft Office Word y Microsoft Office Excel incluyen una nueva característica, Information Rights Management \(IRM\), que puede ayudarle a evitar que personas no autorizadas vean o modifiquen la información confidencial.  Para obtener detalles sobre el funcionamiento de esta nueva función, vea la Ayuda de la aplicación de Office correspondiente.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Ejecutar el código subyacente de los documentos con permisos restringidos  
 Si su solución contiene un documento o libro que utilice IRM, de forma predeterminada, Word y Excel no permiten la ejecución de ningún código.  Si el usuario es el autor del documento o dispone de acceso de tipo Control total, puede cambiar este ajuste predeterminado para que funcione su solución.  Para obtener más información, vea [Cómo: Permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
 IRM impide el uso de <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ServerDocument> para recuperar o manipular datos almacenados en memoria caché en el documento.  
  
## Los usuarios finales restringen los permisos a los documentos que utilizan extensiones de código administrado  
 Cualquier usuario con acceso de tipo Control total del documento o del libro en su solución puede utilizar IRM para restringir los permisos.  Por ejemplo, si un usuario del departamento de contabilidad utiliza una solución que rellena automáticamente una hoja de cálculo con los datos de la base de datos, ese usuario puede desear restringir los permisos a acceso de sólo cambio para las personas de su departamento y de sólo lectura para el resto.  Cuando el usuario agrega permisos restringidos, de forma predeterminada, el código subyacente de la hoja de cálculo no se puede ejecutar y la hoja no se rellenará con los datos.  
  
 Para solucionar el problema, un usuario con control total para el documento o el libro debe cambiar la configuración de permisos predeterminada para permitir el acceso mediante programación al modelo de objetos.  Para obtener más información, vea [Cómo: Permitir que el código se ejecute en documentos con permisos restringidos](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md).  
  
## Vea también  
 [Protección de documentos en soluciones de nivel de documento](../vsto/document-protection-in-document-level-solutions.md)   
 [Protección mediante contraseña en documentos de Office](../vsto/password-protection-on-office-documents.md)   
 [Asegurar las soluciones de Office](../vsto/securing-office-solutions.md)   
 [Implementar una solución de Office](../vsto/deploying-an-office-solution.md)   
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)  
  
  