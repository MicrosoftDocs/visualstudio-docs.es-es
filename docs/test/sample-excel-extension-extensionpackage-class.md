---
title: "Extensi&#243;n de Excel de muestra: ExtensionPackage (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6e45410a-1819-4d54-ac21-7280152f7e3a
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Extensi&#243;n de Excel de muestra: ExtensionPackage (Clase)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esta clase extiende la clase <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage> y proporciona el punto de entrada para una prueba de IU codificada que está probando una hoja de cálculo de [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
## Assembly \(atributo\)  
 El archivo comienza con un atributo assembly que identifica el ensamblado como una extensión de prueba de IU.  
  
```  
[assembly: Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage(  
    "ExcelExtensionPackage",  
    typeof(  
     Microsoft.VisualStudio.Test.Sample.UI.ExtensionPackage))]  
```  
  
 Este atributo declara el nombre de la clase base, el nombre de la clase del paquete y el nombre completo de la clase de paquete de extensión personalizada.  
  
## Propiedades simples  
 Esta clase tiene propiedades que proporcionan valores usados por el marco de pruebas de IU codificadas para identificar y describir la extensión y el ensamblado.  Vea los comentarios del código para obtener más información.  
  
## GetService \(método\)  
 El método <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage.GetService%2A> es el punto de entrada única usado por el marco de pruebas de IU codificadas para obtener acceso al administrador de tecnología, el proveedor de propiedades y el filtro de acción, tal y como identifica la clase base para cada objeto.  
  
## Vea también  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [Extender las pruebas de IU codificadas y las grabaciones de acciones para la compatibilidad con Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)