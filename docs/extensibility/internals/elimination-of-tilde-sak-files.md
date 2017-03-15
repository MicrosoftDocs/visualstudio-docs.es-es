---
title: "Eliminaci&#243;n de ~ SAK archivos | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "archivos temporales"
  - "~ sak archivos"
  - "en los complementos de control de origen ~ archivos SAK"
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Eliminaci&#243;n de ~ SAK archivos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

En el Control de origen API de complemento 1,2, los archivos de ~SAK han sido reemplazados por los marcadores de la capacidad y las funciones que detectan si un complemento de control de código fuente admite el archivo de MSSCCPRJ y comprobaciones compartidas.  
  
## archivos de ~SAK  
 Visual Studio .NET 2003 creado archivos temporales prefijados con el ~SAK.  estos archivos se utilizan para determinar si un complemento de control de código fuente admite:  
  
-   el archivo de MSSCCPRJ.SCC.  
  
-   Desprotecciones \(compartidos\).  
  
 Para los complementos que admiten las funciones avanzadas proporcionados en el Control de origen la API del complemento de 1,2, el IDE pueden detectar estas funciones sin crear archivos temporales con el uso de las nuevas funciones, marcadores, y las funciones, detalladas en las siguientes secciones.  
  
## Nuevos marcadores de capacidad  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## nuevas funciones  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 Si un complemento de control de código fuente admite desprotecciones \(compartidos\) múltiples, después declara la capacidad de `SCC_CAP_MULTICHECKOUT` e implementa la función de `SccIsMultiCheckOutEnabled` .  Esta función se denomina siempre que una operación de salida aparezca en proyectos controlados mediante código fuente cualquiera de los.  
  
 Si un complemento de control de código fuente admite la creación y uso de un archivo de MSSCCPRJ.SCC, se declara la capacidad de `SCC_CAP_SCCFILE` e implementa [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md).  esta función se denomina con una lista de archivos.  La función devuelve `TRUE/FALSE` para que cada archivo indica si Visual Studio debe utilizar un archivo de MSSCCPRJ.SCC para él.  Si el complemento de control de código fuente decide no admitir estas nuevas capacidades y funciones, puede utilizar la siguiente clave del Registro para deshabilitar la creación de estos archivos:  
  
 \[\=dword HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateTemporaryFilesInSourceControl ": 00000001  
  
> [!NOTE]
>  Si la clave del Registro se establece en DWORD: 00000000, es equivalente a la clave que es inexistente, y Visual Studio intentará crear archivos temporales.  Sin embargo, si la clave del Registro se establece en DWORD: 00000001, Visual Studio no intenta crear archivos temporales.  En su lugar se supone que el complemento de control de código fuente no admite el archivo de MSSCCPRJ.SCC y no admite desprotecciones compartidos.  
  
## Vea también  
 [Novedades de la API de complemento de origen Control versión 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)