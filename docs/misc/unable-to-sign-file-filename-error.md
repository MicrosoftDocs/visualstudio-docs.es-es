---
title: "No se puede firmar el archivo &#39;&lt;nombreDeArchivo&gt;&#39;: &lt;error&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31028"
  - "vbc31028"
helpviewer_keywords: 
  - "BC31028"
ms.assetid: 2cb22e75-5ee2-4e07-afc0-680a0bd543d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No se puede firmar el archivo &#39;&lt;nombreDeArchivo&gt;&#39;: &lt;error&gt;
Error al intentar firmar el archivo especificado. Este error puede deberse a varias razones:  
  
-   Permisos insuficientes.  
  
-   Faltan archivos del sistema necesarios para la firma con Authenticode.  
  
-   Una referencia a un certificado o un archivo de clave privada inexistentes.  
  
-   Ortografía incorrecta de un nombre de archivo o una dirección URL.  
  
 **Identificador de error:** BC31028  
  
### Para corregir este error  
  
1.  Escriba los nombres de archivo de clave privada y de certificado correctos.  
  
2.  Si usa la firma con Authenticode, compruebe que los archivos Signcode.exe y Javasign.dll están presentes y que no se estableció el atributo de solo lectura.  
  
3.  Asegúrese de que tiene el permiso `Write` para el archivo.  
  
## Vea también  
 [File Signing Tool \(Signcode.exe\)](http://msdn.microsoft.com/es-es/2d299154-34ea-41ba-ad12-17075bb7e1db)   
 [Deployment and Authenticode Signing](http://msdn.microsoft.com/es-es/ecc3f059-da2e-445b-9b87-5b2978e2f8b2)