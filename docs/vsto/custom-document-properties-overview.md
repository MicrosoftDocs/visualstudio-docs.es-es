---
title: "Informaci&#243;n general sobre propiedades personalizadas del documento"
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
  - "_AssemblyLocation (propiedad)"
  - "_AssemblyName (propiedad)"
  - "propiedades de documento personalizadas"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], propiedades personalizadas"
  - "documentos [desarrollo de Office en Visual Studio], propiedades personalizadas"
  - "documentos de Office [desarrollo de Office en Visual Studio], propiedades personalizadas"
ms.assetid: 9a215904-b760-4a49-93e8-a1a708ce0526
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Informaci&#243;n general sobre propiedades personalizadas del documento
  Cuando se compila un proyecto de nivel de documento, Visual Studio agrega dos propiedades personalizadas al documento en el proyecto: \_AssemblyLocation y \_AssemblyName.  Cuando el usuario abre un documento, la aplicación de Microsoft Office comprueba si el documento tiene estas propiedades personalizadas.  Si existen en el documento, la aplicación carga el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], que inicia la personalización.  Para obtener más información, vea [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## \_AssemblyName  
 Esta propiedad contiene el CLSID de una interfaz en el componente de cargador de soluciones del [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  El valor de CLSID es 4E3C66D5\-58D4\-491E\-A7D4\-64AF99AF6E8B.  Este valor no se debe modificar nunca.  
  
## \_AssemblyLocation  
 Esta propiedad contiene una cadena que proporciona los detalles sobre el manifiesto de implementación para la personalización.  Para obtener más información sobre los manifiestos, vea [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 El valor de propiedad\_AssemblyLocation puede tener diferentes formatos, dependiendo de cómo se implemente la solución:  
  
-   Si la solución se publica para que se instale desde un sitio web, una ruta de acceso UNC o una unidad de CD o USB, la propiedad \_AssemblyLocation tiene el formato *rutaDeAccesoDelManifiestoDeImplementación*|*identificadorDeLaSolución*.  La siguiente cadena es un ejemplo:  
  
     file:\/\/deployserver\/MyShare\/ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9  
  
-   Si se ejecuta o depura la solución desde Visual Studio, la propiedad \_AssemblyLocation tiene el formato *nombreDelManifiestoDeImplementación*|*identificadorDeLaSolución*|vstolocal.  La siguiente cadena es un ejemplo:  
  
     ExcelWorkbook1.vsto|74744e4b\-e4d6\-41eb\-84f7\-ad20346fe2d9|vstolocal  
  
 *identificadorDeLaSolución* es un GUID que el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usa para identificar la solución.  *SolutionID* se genera automáticamente al compilar el proyecto. El término **vstolocal** indica a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] que el ensamblado debe cargarse en la misma carpeta que el documento.  
  
## Vea también  
 [Arquitectura de las soluciones de Office en Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md)   
 [Manifiestos de implementación y aplicación en soluciones de Office](../vsto/application-and-deployment-manifests-in-office-solutions.md)   
 [Cómo: Publicar una solución de Office usando ClickOnce](http://msdn.microsoft.com/es-es/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)   
 [Cómo: Crear y modificar propiedades personalizadas para documentos](../vsto/how-to-create-and-modify-custom-document-properties.md)  
  
  